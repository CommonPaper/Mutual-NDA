# Mutual-NDA Verification

This discusses the process of machine-verification of a contract.

### Why is this important?

Since the goal is to provide a standard contract where exactly the same wording in many cases, documents with the exact same structure can give us some benefits.

* If the contract is reused by the same person, one can check that it's the exact same verbiage as used previously... one needn't read and analyze the full text to ensure the terms are the same. This is especially true if minor terms are changed: if they can be located in the separate "Changes" section, it is straightforward to analyze nothing but the changes.

* If the contract is used by many people, others can potentially check the popularity of the contract. This is only possible if there is an accessible index of users of the contract (which is a difficult problem), but there are many social platforms now and in the future that may be reliable, secure stores of this type of information.

### How do I create a verifiable contract?

There are two artifacts that are useful:

* The base contract, which is exactly the text [here](https://raw.githubusercontent.com/CommonPaper/Mutual-NDA/main/Mutual-NDA-preimage-lmd.md). This text can be automatically compared with anyone else's copy to see if it's exactly the same, character-for-character; it can also be cryptographically hashed to get an identifying fingerprint which is even easier to compare (see [the shasum hash here](Mutual-NDA-preimage-lmd.shasum)).

* The full contract, which can be built on top with an approach like [Legal Markdown](https://github.com/compleatang/legalmarkdown). The benefit of this is a single, self-contained document which can be cryptographically signed -- such that the signature can be used for proof of agreement. The construction is simple: add the values for each parameter to the top of the contract, in a standard format called [YAML](https://yaml.org/spec/1.2.2/), enclosed by lines of `---` (three dashes). For example:

    ```
    ---
    Party 1: |
      Muj Axmed Jimcaale Road, Hargeisa, Republic of Somaliland
      Watershed Legal Services, Ltd.
      the Republic of Somaliland
    Party 2: |
      Jawaharlal Nehru Marg opp. Raj Ghat
      Vikram Nagar
      New Delhi, Delhi 110002
      India
    Effective Date: 2022-09-09
    Jurisdiction: Regional Court of Margeisa
    ---
    ```

There are benefits of this type of full contract:

* It is entirely self-contained, so all terms and variables are together and can be sent as one file.

* A program can extract the content and render the English version in any format.

* The full document can be cryptographically signed by each party and shared, so each party holds a copy where the signature can be algorithmically verified. A small hashed-then-signed copy can be put on a public ledger for timestamping and auditability. (Warning: other steps must be taken to keep the contents fully secret, such as inclusion of a random nonce in the document.)

* A program can extract the base contract and quickly check that the contents are exactly as expected, ie. it matches the Common Paper MNDA exactly.

### References

* Legal Markdown, in [go](https://github.com/compleatang/legalmarkdown) and [ruby](https://github.com/compleatang/legal-markdown).
* [YAML](https://yaml.org/spec/1.2.2/)
