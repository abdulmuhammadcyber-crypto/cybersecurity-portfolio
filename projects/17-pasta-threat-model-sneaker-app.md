# PASTA Threat Model for a Sneaker Retail App

## Project description

A growing sneaker company is launching a mobile app that lets buyers browse and
purchase shoes and lets sellers list shoes for sale. The app handles a large amount of
personal and payment information, so the security team was asked to threat model it
before release. I worked through the seven stages of the PASTA framework, which stands
for Process for Attack Simulation and Threat Analysis, to define what the business is
protecting, look at the technologies in scope, map how data moves, and land on a set of
controls that reduce the risk of a breach.

## Stage I: Business objectives

- Run a mobile marketplace where buyers can browse and purchase sneakers and sellers can
  list them, so that the platform generates revenue and keeps both sides coming back.
- Protect the personal and payment information customers hand over, since a leak of card
  data or passwords would break customer trust and expose the company to fines under
  PCI DSS.
- Keep the app and its transactions available and reliable, because downtime or failed
  purchases costs sales and pushes buyers toward competitors.

## Stage II: Technology scope

The app relies on several technologies to move and store user data. Third party
application programming interfaces add features such as payments and shipping without
building them from scratch. Public key infrastructure secures information in transit,
using AES to encrypt sensitive data like card numbers and RSA to exchange keys between
the app and the user's device. SHA-256 hashes protect stored secrets such as passwords.
Structured query language, or SQL, runs the database that holds the sneaker listings,
the sellers, and the data pulled during a purchase.

I would evaluate the SQL database first. It is the single place where the most sensitive
data lives, including account details and information touched during payment, and it sits
directly behind user facing inputs like search and login. That exposure to injection and
broken access, combined with the value of what it holds, makes it the highest priority of
the four technologies.

## Stage III: Application decomposition

Stage three breaks the app into its processes and follows the data through each one. Take
the process where a buyer searches for shoes that are for sale. The buyer types a query
in the app, the app sends that request through an API, the request reaches the SQL
database, the database returns matching listings, and the results travel back over a PKI
protected connection. During checkout the same buyer submits card data, which AES
encrypts in transit and at rest, while the account password is verified against its
SHA-256 hash rather than stored in the clear. Reviewing the data flow diagram alongside
these technologies shows exactly where user data is exposed and where each protection is
supposed to sit, which is the information the later stages depend on.

## Stage IV: Threats

- Injection attacks against the SQL database. A threat actor could submit crafted input
  through the search or login fields to read, change, or dump records the app never meant
  to expose, including customer and payment data.
- Social engineering aimed at employees. A phishing message or pretext call could trick a
  staff member into handing over credentials or approving access, giving an attacker a way
  around authentication without touching the code at all. Internal system logs are a good
  source of intel for spotting both of these once they start.

## Stage V: Vulnerabilities

- Missing or weak input validation on the fields that reach the database. If the app
  passes user input straight into SQL queries instead of using parameterized statements,
  the search and login forms become an open door for injection.
- Outdated or misconfigured third party API components. A payment or shipping API left on
  a version with a known flaw, or a form that fails to encrypt card data before it is sent,
  gives an attacker a documented weakness to exploit. Resources like the CVE list and OWASP
  are useful for finding issues of this kind.

## Stage VI: Attack tree

Stage six takes the threats and vulnerabilities from the previous steps and lays them out
as an attack tree. The goal at the top, stealing customer payment data, branches into the
different routes an attacker could take to reach it. One branch runs through SQL injection
in an unvalidated input field. Another runs through phishing an employee to steal a
credential, then reusing that access to reach the database. A third branch targets a
vulnerable third party API. Reviewing the attack tree resource makes it clear how a single
weak point connects to the end goal, and real applications like this normally carry large
trees with many more branches than the few shown here.

## Stage VII: Security controls

- Use input validation and parameterized queries so user input can never be executed as
  part of a SQL statement, which closes off the injection path to the database.
- Encrypt data in transit and at rest with the PKI already in scope, keeping AES on
  sensitive fields like card numbers, RSA for key exchange, and TLS across every
  connection between the app and its services.
- Require multi-factor authentication on user and employee accounts so a password stolen
  through phishing or a breach is not enough on its own to get in.
- Turn on security logging, monitoring, and alerting, and keep third party APIs and
  dependencies patched, so a known flaw is closed quickly and an attack in progress is
  caught from the logs instead of discovered after the data is gone.

## Response summary

The PASTA process moved this app from a general worry about a data breach to a specific,
defensible plan. The business needs to run a marketplace, protect customer and payment
data, and stay available. Of the technologies in scope, the SQL database, the APIs, the
PKI encryption, and SHA-256 hashing, the database earned first priority because it holds
the most sensitive data behind user facing inputs. From there the two threats that stand
out are SQL injection and employee social engineering, the two vulnerabilities are weak
input validation and outdated or unencrypted API and payment components, and the four
controls that limit that risk are parameterized queries, encryption across the PKI,
multi-factor authentication, and logging paired with regular patching.
