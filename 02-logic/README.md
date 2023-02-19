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
        s_b <= "101"; 
        s_a <= "110"; 
        wait for 100 ns;
        -- Expected output
        assert ((s_B_greater_A = '0') and
                (s_B_equals_A = '0') and
                (s_B_less_A = '1'))
        -- If false, then report an error
        report "Input combination A=101 B=110 FAILED" severity error;

        -- 2 test case
        s_b <= "110"; 
        s_a <= "110"; 
        wait for 100 ns;
        -- Expected output
        assert ((s_B_greater_A = '0') and
            	(s_B_equals_A = '1') and
          	    (s_B_less_A = '0'))
        -- If false, then report an error
        report "Input combination A=110 B=110 FAILED" severity error;

        -- 3 test case
        s_b <= "110"; 
        s_a <= "100"; 
        wait for 100 ns;
        -- Expected output
        assert ((s_B_greater_A = '1') and
                (s_B_equals_A = '0') and
                (s_B_less_A = '0'))
        -- If false, then report an error
        report "Input combination A=110 B=100 FAILED" severity error;

        -- 4 test case
        s_b <= "101"; 
        s_a <= "000"; 
        wait for 100 ns;
        -- Expected output
        assert ((s_B_greater_A = '1') and
                (s_B_equals_A = '0') and
                (s_B_less_A = '0'))
        -- If false, then report an error
        report "Input combination A=101 B=000 FAILED" severity error;

        -- 5 test case with intentional mistake
        s_b <= "001"; 
        s_a <= "101"; 
        wait for 100 ns;
        -- Expected output
        assert ((s_B_greater_A = '0') and
                (s_B_equals_A = '1') and
                (s_B_less_A = '0'))
        -- If false, then report an error
        report "Input combination A=001 B=101 FAILED" severity error;

        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;
```

2. Link to your public EDA Playground example:

   [https://www.edaplayground.com/...](https://www.edaplayground.com/...)
