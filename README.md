pragma circom 2.0.0;

template GivenCircuit () {  

   signal input a;
   signal input b;
   signal X;
   signal Y;
   signal output Q;

   // Component gates used to create custom curcuit
   component andGate = AND();
   component notGate = NOT();
   component orGate = OR();

   // Circuit Logic
   andGate.a <== a;
   andGate.b <== b;
   X <== andGate.out;

   notGate.in <== b;
   Y <== notGate.out;

   orGate.a <== X;
   orGate.b <== Y;
   Q <== orGate.out;

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

component main = GivenCircuit();


///





pragma circom 2.0.0;

template Circuit () {
    signal input a;
    signal input b;
    signal x;
    signal y;
    signal output q;
    component andGate = AND();
    component notGate = NOT();
    component orGate = OR();
    andGate.a <== a;
    andGate.b <== b;
    notGate.in <== b;
    orGate.c <== andGate.out;
    orGate.d <== notGate.out;
    x <== orGate.out;
    y <== notGate.out;
    q <== orGate.out;
}

template AND() {

    signal input x;
    signal input y;
    signal output out;
    out <== x * y;
}

template NOT() {
    signal input in;
    signal output out;
    out <== 1 + in - 2 * in;
}

template OR() {
    signal input x;
    signal input y;
    signal output out;
    out <== x + y - x * y;
}

component main = Circuit();

////

pragma circom 2.0.0;

template Circuit () {

    // Signal input a and b

    signal input a;
    signal input b;

    // Intermidiate signals x and y
    signal x;
    signal y;

    //output of whole circuit
    signal output q;

    // function for gates
    component andGate = AND();
    component notGate = NOT();
    component orGate = OR();

    //logic
    andGate.a <== a;
    andGate.b <== b;
    x <== andGate.out;

    notGate.in <== b;
    y <== notGate.out;

    orGate.c <== x;
    orGate.d <== y;
    q <== orGate.out;
}

template AND() {

    signal input x;
    signal input y;
    signal output out;

    // AND gate
    out <== x * y;
}

template NOT() {
    signal input in;
    signal output out;

    // NOT gate 
    out <== 1 + in - 2 * in;
}

template OR() {
    signal input x;
    signal input y;
    signal output out;

    // OR gate 
    out <== x + y - x * y;
}

component main = Circuit();