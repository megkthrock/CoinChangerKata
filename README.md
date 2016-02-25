# CoinChangerKata
Coin Changer Kata

The Coin Changer Kata is supposed to be able to take in a certain coin value and be able to return how many quarters, dimes, nickels, and pennies are required to make up that amount of change. In our first test, we just wanted to have a change due of 1 cent and expect to get 1 penny back. 
def change(change_due)
coins = {"quarters" => 0, "dimes" => 0, "nickels" => 0, "pennies" => 1}
end
Using the least amount of code, we defined “change” taking in the parameter “change_due” and created a hash containing each coin and setting each value to zero except the need for 1 penny.
To test the outcome of 3 cents of change due, we needed to adjust the code. To do it as simply as possible:
def change(change_due)
coins = {"quarters" => 0, "dimes" => 0, "nickels" => 0, "pennies" => change_due}
end
By changing the value of “pennies” to “change_due, it now takes in the cents of “change_due” and allows both tests of 1 and 3 cents to pass.
Next, the test of 5 cents needed to pass. Because of the way our code is set now, the code would return 5 pennies. We want it to return 1 nickel. To modify the code we made these changes:
def change(change_due)
    coins = {"quarters" => 0, "dimes" => 0, "nickels" => 0, "pennies" => 0}
    if change_due >= 5
        coins["nickles"] = 1
    else	
        coins["pennies"]=        change_due
     end
     coins
end 	
    With an if/else statement, we have set all values in the hash to zero. Now, different values can be passed in as needed. By saying the change is greater than or equal to 5, it tell us we need to replace 0 nickels in the hash to 1. Then, if change is less than 5 cents, it will just replace pennies value with “change_due”. For now, the tests pass.
          To test for change of 6 cents, the code must be altered again. To add the least amount of code, we added:
              coins["pennies"] = change_due – 5

under line 5 to allow for numbers over 5. It will take change due and subtract the value of the nickel leaving us how many pennies are needed.
       To test the results for 10 cents, the code needed to be altered again:
if change_due >= 10
    coins["dimes"] = 1
    coins["pennies"] = change_due – 10
elsif change_due >= 5

        By adding if the change due is greater than or equal to 10, we can now set the value of dimes to 1 and change pennies by subtracting that value of the dime.  Because we added the if statement ahead of the one for 5, it will try that if statement first and if does not satisfy the requirement it will move on to the elsif or else statement. These adjustments pass the current tests.
	Tests for change of 11 passed smoothly with no adjustments necessary. To pass the test of change for 16 cents, the code needed to be altered again.



if change_due >= 15
   coins["dimes"] = 1
   coins["nickles"] = 1
   coins["pennies"] = change_due – 15
elsif change_due >= 10

	Just as we did in the previous altering, by adding the if statement change due is greater than or equal to 15, we add 1 dime, 1 nickel, and get our pennies by subtracting 15 from change due. If the number is not greater than or equal to 15 it will move on to the next elsif statement and so on.
	After testing for change of 16 cents, we decided to reconfigure the code to make it applicable for higher values of change and easier to alter later.
dimes = 10
nickles = 5
pennies = 1
	if change_due >= dimes
		coins["dimes"] = 1
		change_due = change_due - dimes
	end
if change_due >= nickles
coins["nickles"] = 1
change_due = change_due - nickles
end
if change_due >= pennies
coins["pennies"] = change_due
end

Now by giving variables dimes, nickels, and pennies values we can use them in place of actual numbers.  We also changed each level of coins into their own “if” statements.  As of now, all the tests had passed. It will ask if the change due is greater than equal to 10, and if it does not satisfy, it will move on to the next “if” statements until it is satisfied.
When we reached the test for change of 20, we realized that our code would not be able to give us 2 dimes.  So by changing:
while change_due >= dimes
coins["dimes"] = coins["dimes"] + 1
change_due = change_due - dimes
end
These changes were made to each “if “ statement.  Now it will keep running through the while until it no longer is satisfied and move on to the next while loop.  We also changed the second line of code so that after the value of coins[“dimes] is altered, if the loop runs again it will add the  previous dime. This code works the same for nickels and pennies.
Once we exceed the change of 24 cents we would need to add quarters.
quarters = 25

	We added the value of quarters ahead of dimes and also added a while loop in the same format as the others in front of dimes. By testing for change of 94 cents we were able to see each coin used and it did pass.
Instead of having four separate while loops, it would make sense to simplify it.
def change(change_due)
coins = {"quarters"=>0, "dimes"=>0, "nickles"=>0, "pennies"=>0}
coin_values={"quarters"=>25,"dimes"=>10,"nickles"=>5,"pennies"=>1

coin_values.each do |coin, value|
while change_due >= value
coins[coin] = coins[coin] + 1
change_due = change_due - value
end
end

First, we added a second hash to represent the cent value of each coin.  By doing the coin_values.each method, it will go through each element within that hash. The |coin, value| represents the key which is coin, and the value of that key which is value.  Now, we add a while loop to ensure it will run the same coin until it is no longer applicable.  So in the instance of “quarters” it would take the value of “quarters”, 25, and apply that where it says >=value. Then, our hash “coins” will take the value of the key “coin” and continue to add quarters until it no longer applies. The next line updates what is left of the change due by subtracting the value each time.  It would then go through every element in the coin_value hash until change due equals 0.






