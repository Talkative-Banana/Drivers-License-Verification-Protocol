# Driver’s License Verification Protocol

## Project Overview

This project implements an on-the-go verification protocol for driver's licenses using RSA-based digital signatures. The protocol allows Traffic Police Officers to verify the validity of licenses issued by different Regional Transport Offices (RTOs) via digital signatures, ensuring message integrity, authenticity, and non-repudiation. This verification system supports multiple RTOs and a central National Transport Office (TO).

## Table of Contents

1. [Introduction](#introduction)
2. [Project Structure](#project-structure)
3. [Working Schema](#working-schema)
   - [Key Generation](#key-generation)
   - [Encryption](#encryption)
   - [Decryption](#decryption)
4. [Classes and Functionalities](#classes-and-functionalities)
5. [Running the Code](#running-the-code)
6. [Authors](#authors)

## Introduction

The Driver’s License Verification Protocol was developed as part of a project to create a decentralized system that allows Traffic Police Officers to verify licenses on the spot. This system leverages RSA-based digital signatures to ensure document authenticity without requiring a central server to store all license data, providing efficient and secure on-the-go license validation.

## Project Structure

    ├── RSA.py # RSA encryption, decryption, and key generation functions 
    ├── TransportAuthority.py # Handles RTO and National TO functions for verification 
    ├── Client.py # Client (Traffic Police) verification requests 
    ├── SignCert.py # Signs certificates for licenses 
    └── README.md # Project README file


## Working Schema

### Key Generation

RSA key pairs are generated by selecting two large primes \(p\) and \(q\). From these, \(n\) and \(\phi\) are computed to produce a public-private key pair \((e, d)\).

```python
def generate_rsa_keys(self, n_bits=1024):
    p = self.generate_prime(n_bits)
    q = self.generate_prime(n_bits)
    n = p * q
    phi = (p-1) * (q-1)
    e = 65537
    d = mod_inverse(e, phi)
    return ((e, n), (d, n))
```
### Encryption

Messages are encrypted with the RSA public key, allowing secure verification of digital signatures.

### Decryption

Encrypted messages are decrypted with the RSA private key, retrieving the original message for verification.

## Classes and Functionalities

### RSA Class

- **generate_rsa_keys** - Generates RSA key pairs using prime numbers.
- **rsa_encrypt** - Encrypts messages using the public key.
- **rsa_decrypt** - Decrypts encrypted messages using the private key.

### TransportAuthority Class

- **Verify License** - Verifies license authenticity based on digital signatures.
- **Obtain Public Key of RTO** - Requests the public key of a Regional RTO from the National TO when a license is signed by another RTO.

### Client Class

- **Get Document Verified** - Requests license verification from an RTO or National TO.

## Running the Code
- Clone the repository:
  ```
  git clone https://github.com/Talkative-Banana/Drivers-License-Verification-Protocol.git
  cd Driver-s-License-Verification-Protocol
  ```
 - To run the code, you need to keep all the files in a folder, then simple run Client.py using python Client.py in terminals, and TransportAuthority.py using python in another terminal. To generate Signed Certificates another file by the name of SignCert.py is available.
## Authors
Ekansh - IIIT Delhi

Lakshay Bansal - IIIT Delhi
