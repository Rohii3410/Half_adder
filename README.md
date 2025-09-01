# Half Adder – EDA Playground

## 📘 Project Overview
This project demonstrates a **Half Adder** implemented and simulated on [EDA Playground](https://www.edaplayground.com/).  
A Half Adder is a combinational logic circuit that performs addition of two single-bit binary numbers. It produces two outputs:
- **Sum (S)**
- **Carry (C)**

---

## 🔢 Truth Table

| Input A | Input B | Sum (S) | Carry (C) |
|---------|---------|---------|-----------|
|    0    |    0    |    0    |     0     |
|    0    |    1    |    1    |     0     |
|    1    |    0    |    1    |     0     |
|    1    |    1    |    0    |     1     |

---

## 🖥️ Design Code (Verilog)
    verilog
    module half_adder(
       input A, B,
       output Sum, Carry
    );
    assign Sum = A ^ B;     // XOR for Sum
    assign Carry = A & B;   // AND for Carry
    endmodule

## 🧪 Verilog Testbench
    module tb_half_adder;
      reg A, B;
      wire Sum, Carry;

    // Instantiate Half Adder
    half_adder uut (
        .A(A), 
        .B(B), 
        .Sum(Sum), 
        .Carry(Carry)
    );

    initial begin
        $display("A B | Sum Carry");
        $monitor("%b %b |  %b    %b", A, B, Sum, Carry);

        // Test cases
        A=0; B=0; #10;
        A=0; B=1; #10;
        A=1; B=0; #10;
        A=1; B=1; #10;

        $finish;
    end
    endmodule
