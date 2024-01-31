Module half adder(a,b,sum,carry);
Input a;
Input b;
Output sum;
Output carry;
assign sum=a^b;
assign carry=a&b;
endmodule

Test bench code for half adder:
module half_adder_tb;
reg a,b;
wire sum,carry;
half_adder_s uut(a,b,sum,carry);
initial begin
a = 0; b = 0;
#10
b = 0; b = 1;
#10
a = 1; b = 0;
#10
b = 1; b = 1;
#10
$finish();
end
endmodule

module full adder(a,b,ci,sum,cout);
input a,b,ci;
output sum,co;
assign sum=a^b^ci;
assign cout=(a&b)|(b&ci)|(ci&a);
endmodule 

Test bench code for full adder:
module full_adder_tb;
reg a,b,cin;
wire sum,carry;

full_adder_s uut(a,b,cin,sum,carry);

initial begin
a = 0; b = 0; cin = 0;
#10
a = 0; b = 0; cin = 1;
#10
a = 0; b = 1; cin = 0;
#10
a = 0; b = 1; cin = 1;
#10
a = 1; b = 0; cin = 0;
#10
a = 1; b = 0; cin = 1;
#10
a = 1; b = 1; cin = 0;
#10
a = 1; b = 1; cin = 1;
#10
$finish();
end       
endmodule
