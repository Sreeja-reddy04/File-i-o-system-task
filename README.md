# File i/o system_task
## Even parity
### [Test bench]
```bash
`timescale 1ns/1ps
module even_parity;

  integer infile, outfile;   
  reg [7:0] data;           
  reg parity;               
  initial begin
    infile  = $fopen("data_in.txt", "r");
    outfile = $fopen("data_out.txt", "w");
    // Check if files opened correctly
    if (infile == 0 || outfile == 0) begin
      $display("Error: Cannot open input or output file!");
      $finish;
    end
    while (!$feof(infile)) begin
      $fscanf(infile, "%b\n", data);   
      parity = ~(^data);               
      $fdisplay(outfile, "%b", parity); // Write result to output file
    end
    $fclose(infile);
    $fclose(outfile);
    $display("✅ Simulation complete - Parity bits written to data_out.txt");
    $finish;
  end
endmodule
```
## 2's complement
### [Test bench]
```bash
`timescale 1 ns / 1 ps
 module twos_complement;
 integer infile,outfile;
 reg [4:0]d;
 reg [4:0]compl;
  initial begin
 infile=$fopen("data_in1.txt","r");
 outfile=$fopen("data_out1.txt","w");
  if(infile==0||outfile==0)begin
  $display("error file can't be open");
  $finish;
  end
  while(!$feof(infile))
  begin
  $fscanf(infile,"%b\n",d);
  compl=~d+1;
  $fdisplay(outfile,"%b",compl[4:0]);
  end
  $fclose(infile);
  $fclose(outfile);
    $display(" Simulation complete - result bits written to data_out1.txt");
    $finish;
  end 
  endmodule 
```
