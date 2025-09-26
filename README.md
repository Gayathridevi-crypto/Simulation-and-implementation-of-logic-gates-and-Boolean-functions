# Simulation-and-implementation-of-logic-gates-and-Boolean-functions
//====================================================
// Logic Gates Module
//====================================================
module logic_gates (
    input  wire a,    // input A
    input  wire b,    // input B
    output wire and_out,
    output wire or_out,
    output wire not_out,
    output wire nand_out,
    output wire nor_out,
    output wire xor_out,
    output wire xnor_out
);

  // Logic operations
  assign and_out  = a & b;
  assign or_out   = a | b;
  assign not_out  = ~a;       // single-input gate
  assign nand_out = ~(a & b);
  assign nor_out  = ~(a | b);
  assign xor_out  = a ^ b;
  assign xnor_out = ~(a ^ b);

endmodule

//====================================================
// Logic Gates Testbench
//====================================================
`timescale 1ns/1ps

module tb_logic_gates;

  // Test inputs
  reg a, b;

  // Outputs
  wire and_out, or_out, nand_out, nor_out, xor_out, xnor_out, not_out;

  // Instantiate gates
  and  u_and  (and_out,  a, b);
  or   u_or   (or_out,   a, b);
  nand u_nand (nand_out, a, b);
  nor  u_nor  (nor_out,  a, b);
  xor  u_xor  (xor_out,  a, b);
  xnor u_xnor (xnor_out, a, b);
  not  u_not  (not_out,  a);

  // Test procedure
  initial begin
    $display("A B | AND OR NAND NOR XOR XNOR NOT(A)");
    $display("-------------------------------------");

    a = 0; b = 0; #10;
    $display("%b %b |  %b   %b    %b    %b    %b    %b     %b",
              a, b, and_out, or_out, nand_out, nor_out, xor_out, xnor_out, not_out);

    a = 0; b = 1; #10;
    $display("%b %b |  %b   %b    %b    %b    %b    %b     %b",
              a, b, and_out, or_out, nand_out, nor_out, xor_out, xnor_out, not_out);

    a = 1; b = 0; #10;
    $display("%b %b |  %b   %b    %b    %b    %b    %b     %b",
              a, b, and_out, or_out, nand_out, nor_out, xor_out, xnor_out, not_out);

    a = 1; b = 1; #10;
    $display("%b %b |  %b   %b    %b    %b    %b    %b     %b",
              a, b, and_out, or_out, nand_out, nor_out, xor_out, xnor_out, not_out);

    $finish;
  end 
  endmodule
  
