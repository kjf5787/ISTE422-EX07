-----------------------------
CHECKING ACCOUNT TEST FIXTURE 
-----------------------------

How to run it?
- The following command will run CheckingAccountTestFixture.java
    gradle runCheckingFixture --args='src/test/resources/CheckingAccountTest.csv'

Command Language 
- As seen in CheckingAccountTest.csv, the following fields are required in one line representing a test scenario 
    initial value, checks, withdrawals, deposits, final balance, minimum balance, minimum balance fee, run month end
- What do these values mean?
    - initial value: the starting amount in the account, represented as a Double value 
    - checks: the values of checks written to be withdrawn from the account, represented as a single Double value OR a list of Double values separated by |
    - withdrawals: the values of withdrawals to be taken from the account, represented as a single Double value OR a list of Double values separated by |
    - deposits: the values of deposits to be added to the account, represented as a single Double value OR a list of Double values separated by |
    - final balance: the expected final balance in the account after all changes, represented as a Double value 
    - minimum balance: the value that the account cannot drop below without incurring a fee, represented as a Double value  
    - minimum balance fee: the fee that will be charged to the account if the value is below the minimum, represented as a Double value 
    - run month end: whether or not the month end method should be run, represented as a boolean (true or false)
- Some fields may be left empty, but the field must exits
    Example: 1, , , , 1, 0, 0

What kinds of scenarios might this test not run?
- If the user wanted to test several months of fees or other recurring payments 

-----------------------------
SAVINGS ACCOUNT TEST FIXTURE 
-----------------------------

How to run it?
- The following command will run SavingsAccountTestFixture.java
    gradle runSavingsFixture --args='-f src/test/resources/SavingsAccountTest.csv'

Command Language 
- As seen in SavingsAccountTest.csv, the following fields are required in one line representing a test scenario 
    initial value, interest rate, withdrawals, deposits, run month end, final balance, minimum balance, minimum balance fee
- What do these values mean?
    - initial value: the starting amount in the account, represented as a Double value 
    - interest rate: the interest rates for a number of months, represented as a Double value OR a list of Double values separated by |
    - withdrawals: the values of withdrawals to be taken from the account, represented as a single Double value OR a list of Double values separated by |
    - deposits: the values of deposits to be added to the account, represented as a single Double value OR a list of Double values separated by |
    - run month end: the number of times to run the month end function, represented as an int
    - final balance: the expected final balance in the account after all changes, represented as a Double value 
    - minimum balance: the value that the account cannot drop below without incurring a fee, represented as a Double value  
    - minimum balance fee: the fee that will be charged to the account if the value is below the minimum, represented as a Double value 
- The interests rates are represented as a decimal (ex. .10 to represent 10%), NOT a percent (ex. 10 to represent 10%)
- Some fields may be left empty, but the field must exits
    Example: 100, 0.10, , , 1, 100.83, 0, 0
- A limitation: the number of interest rates in the list MUST be the same as the value of run month end
    - Ex: if run month end is 3, three interest rates must be provided

What kinds of scenarios might this test not run?
- If the user wanted to test different deposits or withdrawals for specific months
    - The program currently runs the deposits and withdrawls all at once, then calculates the interest or takes fees for each month