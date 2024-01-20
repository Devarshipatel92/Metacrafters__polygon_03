## What is Zero-Knowledge?

Zero Knowledge is a term that refers to a proving system where a claim can be verified without providing details about the claim. Typically when referring to Zero Knowledge, we are referring to Zero Knowledge proofs or ZKPs.

### Zero-Knowledge Proofs

Zero-knowledge proofs (ZKPs) are a cryptographic technique that allows one party to prove to another party that they know a piece of information, without revealing any additional information about that knowledge beyond what is necessary for the proof.

### Simple Example

To wrap your head around the idea of a ZKP let’s take a look at the Ethereum ECDSA (Elliptic Curve Digital Signature Algorithm) Signature. One party proves they know a private key without revealing the private key. The proof is the signature generated, which any verifying party can verify.

## ZKP Properties:

1. **Completeness:** If something is true, the system should correctly show that it's true.
    
2. **Soundness:** If something is false, the system should correctly show that it's false, no matter what.
    
3. **Zero-Knowledge:** The system should only reveal whether something is true or false, without giving away any extra information.

## Prover and Verifier:

In a ZKP, the party making the proof, **the prover**, demonstrates to the other party, **the verifier**, that they possess a specific piece of information, without revealing any additional information about that information. The proof can be constructed in such a way that the verifier can be confident that the prover knows the information, but cannot determine what the information actually is.

Imagine you have a secret and want to prove it to a friend without actually telling them what the secret is. You (the prover) show your friend (the verifier) some evidence or proof that you know the secret. This proof convinces your friend that you really do know the secret, but it doesn't spill the beans on what the secret is.

So, the prover convinces the verifier they know something special without giving away what that something is. It's like showing you have a key without showing which lock it opens.
### Polygon ID

The Polygon ID framework is a great application to show the roles that **verifiers** and **provers** play. In the following diagram, the Identity holder plays the role of the **prover**, which provides proof of ownership of some Verifiable Credential (VC). The verifier in the diagram accepts the proof and verifies that the **prover** does hold the VC.

ZKPs have many practical applications, particularly in the field of privacy-preserving computation. They can be used to prove things like ownership of a secret key, membership in a set, or the correctness of a computation, without revealing any additional information that could be used to compromise privacy. This has led to many developments of Layer 2 scaling solutions and most recently the zkEVM.

The development of ZKPs has been an important advance in the field of cryptography and has opened up many new possibilities for secure, private computation. However, they can be complex to implement and use, and require careful attention to security considerations in order to ensure that they are used effectively.

### zkSNARKS:

1. **Zero-Knowledge:** You can prove you know something without actually revealing what it is.
    
2. **Succinct:** The proof is quick to check and doesn't take up much space.
    
3. **Non-Interactive:** No back-and-forth is needed. The proof is sent once, and that's it.
    
4. **Argument:** Cheating is highly unlikely. The proof is reliable.
    
5. **Knowledge:** It's very unlikely to make a proof without knowing the secret.
    

**Note:** zkSNARKS are fast and small but need a trusted setup, which means a shared key created with trust among participants.

zKsnarks :- Zero Knowledge Succinct non interactive Argument Knowledge
### zkSTARKS:

1. **Zero-Knowledge:** Like zkSNARKS, you can prove something without revealing the actual details.
    
2. **Scalable:** The time it takes to prove and verify doesn't grow much, even as what you're proving gets bigger.
    
3. **Transparent:** Relies on verifiable randomness, not trusted setups. This makes it different from zkSNARKS.

**Note:** zkSTARKS have larger proofs than zkSNARKS, but they are faster for proving..
### Bulletproofs:

1. **Similar to SNARKS:** It lets you prove something without revealing the details.
    
2. **No Trusted Setup:** Unlike zkSNARKS, it doesn't need a shared key setup. It's trustless.
    
3. **Larger Proofs:** The proofs are bigger compared to zkSNARKS.

**Note:** Bulletproofs are good for certain types of proofs (like range proofs) and are used by projects like Monero.