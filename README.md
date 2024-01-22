## Project Objective 

Imagine that you wake up, check your email, and you see an interesting task: Polygon is asking you to design a new zkSNARK circuit that implements some logical operations. 
You need to implement the circuit and deploy a verifier on-chain to verify proofs generated from this circuit


## ZKsnark Circuit Explanation

![Assessment_b05f6ed658](https://github.com/Devarshipatel92/Metacrafters__polygon_03/assets/157242215/95d58fe0-9c23-4b7c-9292-2ead258ce37b)

The circuit functions by processing two input signals, A and B, which act as operands for the computation. It employs three specific logic gates—AND, NOT, and OR—each established as separate templates. Two intermediary signals, X and Y, are produced as results from the AND and NOT gates, respectively. 
The ultimate output signal, Q, is calculated through the OR gate, utilizing inputs obtained from the intermediary signals.

## Circuit Code Explanations
```circom
pragma circom 2.0.0;

/*This circuit template checks that c is the multiplication of a and b.*/  

template Multiplier2 () {  

   // Declaration of signals.  
   signal input a;  
   signal input b;
   signal x;  
   signal y;  
   signal output c;

   //component
   component andGate = AND();
   component notGate = NOT();
   component orGate = OR();

   // Logic From AND to singals
   andGate.a <== a;
   andGate.b <== b;
   x <== andGate.out;

   // Logic From Signals to Not Gate 
   notGate.in <== b;
   y <== notGate.out;

   //Logic From Not gate to Output C
   orGate.a <== x;
   orGate.b <== y;
   c <== orGate.out;

}

template AND() {
    signal input a;
    signal input b;
    signal output out;

    out <== a*b;
}

template NOT() {
    signal input in;
    signal output out;

    out <== 1 + in - 2*in;
}

template OR() {
    signal input a;
    signal input b;
    signal output out;

    out <== a + b - a*b;
}

component main = Multiplier2();
```


This Circom code defines a circuit template named Multiplier2 that serves the purpose of verifying whether the output signal c is the result of multiplying two input signals, a and b. The circuit is designed with a set of signals, including a, b, x, y, and c, representing the operands, intermediate values, and the final output. Additionally, three logic gate components—andGate, notGate, and orGate—are declared to perform the necessary logical operations.

The code establishes connections between signals and gates to articulate the logic of the multiplier circuit. The andGate component takes inputs a and b and produces an output, x. The notGate component, taking input b, generates an output, y. The orGate component then combines the outputs x and y to produce the final result stored in signal c.

Furthermore, the code provides logic templates for the three types of gates (AND, NOT, OR). The AND template computes the logical AND of inputs a and b, the NOT template calculates the logical NOT of the input in, and the OR template determines the logical OR of inputs a and b.

Finally, the main component named main is instantiated from the Multiplier2 template, representing the entry point for the circuit. In essence, this Circom code encapsulates a multiplier circuit with specified logic gates and connections, ensuring that the output signal c accurately reflects the multiplication of input signals a and b.


## Installation Guide

Install Node.js packages using npm:
```
npm i
```
This command installs the necessary Node.js packages specified in the package.json file.

Run the Circom compiler using npx:

```
npx hardhat circom
```
This command compiles the Circom code into an arithmetic circuit that can be used in your Ethereum project.

Deploy the smart contract using Hardhat on the Mumbai network:
```
npx hardhat run script/deploy.ts --network mumbai
```

This command executes the deployment script located at script/deploy.ts using Hardhat and deploys the smart contract on the Mumbai Ethereum test network.

## Why we use ZKsnarks Circuit

zk-SNARK (Zero-Knowledge Succinct Non-Interactive Argument of Knowledge) circuits are employed for their ability to enhance privacy and efficiency in cryptographic applications. 
By enabling users to prove the validity of computations without revealing sensitive information, zk-SNARKs contribute to robust privacy-preserving solutions, crucial for applications ranging from confidential transactions in blockchain networks to secure data verification and supply chain tracking. 
Their succinct proofs enable quick verification, enhancing scalability and reducing computational overhead, making zk-SNARKs a valuable tool for ensuring data integrity and facilitating interoperability across diverse platforms and decentralized applications.
