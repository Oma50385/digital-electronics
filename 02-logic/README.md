# Lab 2: ROMAN LUNIN

### 2-bit comparator

1. Karnaugh maps for other two functions of 2-bit comparator:

  B is greater than A:

   ![K-maps](https://github.com/Oma50385/digital-electronics/blob/main/02-logic/BisgraterthanA.png)

   B is less than A:

   ![K-maps](https://github.com/Oma50385/digital-electronics/blob/main/02-logic/BislessthanA.png)

2. Mark the largest possible implicants in the K-map and according to them, write the equations of simplified SoP (Sum of the Products) form of the "greater than" function and simplified PoS (Product of the Sums) form of the "less than" function.

   ![Logic functions](https://github.com/Oma50385/digital-electronics/blob/main/02-logic/CodeCogsEqn%20(1).gif)

### 4-bit comparator

1. Listing of VHDL stimulus process from testbench file (`testbench.vhd`) with at least one assert (use BCD codes of your student ID digits as input combinations). Always use syntax highlighting, meaningful comments, and follow VHDL guidelines:

   Last two digits of my student ID: **54**

```vhdl
   p_stimulus : process
	begin
		-- Report a note at the beginning of stimulus process
		report "Stimulus process started" severity note;

		-- first test case
        s_b <= "0101"; 
        s_a <= "0100"; 
        wait for 100 ns;
        -- Expected output
        assert ((s_B_greater_A = '1') and
                (s_B_equals_A = '0') and
                (s_B_less_A = '0'))
        -- If false, then report an error
        report "Input combination A=0100 B=0101 FAILED" severity error;

        -- 2 test case
        s_b <= "0110"; 
        s_a <= "0110"; 
        wait for 100 ns;
        -- Expected output
        assert ((s_B_greater_A = '0') and
            	(s_B_equals_A = '1') and
          	    (s_B_less_A = '0'))
        -- If false, then report an error
        report "Input combination A=0110 B=0110 FAILED" severity error;

        -- 3 test case
        s_b <= "0110"; 
        s_a <= "0100"; 
        wait for 100 ns;
        -- Expected output
        assert ((s_B_greater_A = '0') and
                (s_B_equals_A = '1') and
                (s_B_less_A = '0'))
        -- If false, then report an error
        report "Input combination A=0110 B=0100 FAILED" severity error;

        -- 4 test case
        s_b <= "0101"; 
        s_a <= "0000"; 
        wait for 100 ns;
        -- Expected output
        assert ((s_B_greater_A = '1') and
                (s_B_equals_A = '0') and
                (s_B_less_A = '0'))
        -- If false, then report an error
        report "Input combination A=0000 B=0101 FAILED" severity error;

        -- 5 test case with intentional mistake
        s_b <= "0001"; 
        s_a <= "0101"; 
        wait for 100 ns;
        -- Expected output
        assert ((s_B_greater_A = '0') and
                (s_B_equals_A = '0') and
                (s_B_less_A = '1'))
        -- If false, then report an error
        report "Input combination A=0101 B=0001 FAILED" severity error;

        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;
```

2. Link to your public EDA Playground example:

   [https://www.edaplayground.com/...](https://www.edaplayground.com/x/ivAs)
