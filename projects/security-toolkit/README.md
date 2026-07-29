# Quantum Password Hasher and Security Toolkit

## Overview

This project is a browser based security toolkit that I built to demonstrate practical applied cryptography and secure client side design. The centerpiece is a password hasher that uses quantum resistant hashing, and it is supported by a verification tool, a password strength analyzer, a secure password generator, and a general purpose hash generator. The entire tool is a single HTML file with no external dependencies and no network activity, which means it can be opened offline and audited by reading the source directly.

## Why the hashing is described as quantum resistant

Public key systems such as RSA and elliptic curve cryptography are vulnerable to Shor's algorithm, which a sufficiently large quantum computer could use to break them efficiently. Symmetric primitives and cryptographic hash functions are in a much stronger position. The best known quantum attack against them is Grover's algorithm, which only provides a quadratic speedup. In practical terms that means a 512 bit hash still retains roughly 256 bits of security against a quantum adversary, which is far beyond any feasible attack. The hasher is built on PBKDF2 with HMAC SHA 512 for exactly this reason, so it stays sound even under the assumption that large scale quantum computing arrives.

## How the password hasher works

When a password is entered, the tool generates a fresh 128 bit random salt using the cryptographically secure generator in the browser. It then runs PBKDF2 with the selected hash function and iteration count to derive the final digest. The result is returned as a self describing string in the format pbkdf2, algorithm, iterations, salt, and hash, with the salt and hash encoded in Base64. Because a new salt is produced on every run, hashing the same password twice produces different output, which is the behavior you want because it defeats precomputed rainbow tables and makes identical passwords indistinguishable in storage.

The default iteration count is set high to slow down offline brute force attempts, and the user can raise it further. This mirrors how modern systems store credentials, where the goal is to make each guess expensive rather than to hide a reversible secret.

## Verification

The verify tab accepts a stored hash string and a candidate password, parses out the algorithm, iteration count, and salt, recomputes the derivation, and compares the result. The comparison is performed in constant time so that the amount of time taken does not leak information about how many leading bytes matched. This is a small but important detail that prevents timing side channel attacks against the check.

## Supporting utilities

The strength analyzer estimates entropy from the character pool and the length of the password and reports an offline cracking time under a strong attacker model. The generator produces passwords using the secure random number generator rather than a predictable pseudo random source. The hash generator computes SHA 256, SHA 384, and SHA 512 digests of arbitrary text for integrity checking, and it clearly labels SHA 1 as legacy so it is not mistaken for a security control.

## Security design decisions

Everything runs locally in the browser. No password, hash, or piece of input is transmitted, logged, or stored anywhere, and this can be confirmed by viewing the page source and observing that there are no fetch or network calls. All cryptographic work relies on the Web Crypto API that ships with modern browsers rather than a hand rolled implementation, because reusing vetted primitives is safer than writing your own. These choices reflect the principle that a security tool should be transparent, auditable, and conservative in the primitives it depends on.

## Running it

Open index.html in any modern browser, or host the folder with a static server. There is no build step and no installation.
