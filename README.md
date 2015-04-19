# Bank-Transaction-Java-

import java.util.*;
public class BankTransaction {
	public static void main(String[] args){
		
		//Variables needed throughout this code
		String userReply;
		String userAnswer = "yes";
		double[] transactionHistory = new double[30];
		int i = 0;
		double sumDeposit = 0;
		double numDeposit = 0;
		double sumWithdraw = 0;
		double numWithdraw = 0;
		Scanner keyboard = new Scanner(System.in);
		double currentBalance = 0;
		
		//Welcoming the user
		System.out.println("Welcome to Heel Banking!");
		
		//While loop: keeps asking if the user wants to continue
		while(userAnswer.equalsIgnoreCase("yes")){
			System.out.println("What kind of transaction would you like to do?");
			userReply = keyboard.nextLine();
		
			//Actions the user wants to take
			if(userReply.equalsIgnoreCase("deposit")){
				System.out.println("How much money would you like to deposit?");
				//40enter
				transactionHistory[i] = keyboard.nextDouble();
				//enter
				keyboard.nextLine();
				sumDeposit = sumDeposit + transactionHistory[i];
				numDeposit++;
				currentBalance = currentBalance + transactionHistory[i];
				i++;
				
				//if balance goes to negative
				if(currentBalance < 0){
					System.out.println("Your current balance has reached negative!");
					System.out.println("A penalty of $20 will be applied to your account.");
					currentBalance = currentBalance - 20;
				}
			}
			else if(userReply.equalsIgnoreCase("withdraw")){
				System.out.println("How much money would you like to withdraw?");
				transactionHistory[i] = keyboard.nextDouble() * -1;
				keyboard.nextLine();
				sumWithdraw = sumWithdraw + transactionHistory[i];
				numWithdraw++;
				currentBalance = currentBalance + transactionHistory[i];
				i++;
				
				//if balance goes to negative
				if(currentBalance < 0){
					System.out.println("Your current balance has reached negative!");
					System.out.println("A penalty of $20 will be applied to your account.");
					currentBalance = currentBalance - 20;
				}
					
				}
			
			else if(userReply.equalsIgnoreCase("print")){
				System.out.println("Below are your three most recent transactions:");
				System.out.println(transactionHistory[i-1]);
				System.out.println(transactionHistory[i-2]);
				System.out.println(transactionHistory[i-3]);
				System.out.println("Current Balance: " + currentBalance);
				System.out.println("Average Deposit Amount: " + sumDeposit / numDeposit);
				System.out.println("Average Withdraw Amount: " + sumWithdraw / numWithdraw);
			}
			else{
				System.out.println("Unrecognized Option");
			}
		//Asking if the user wants to continue
			System.out.println("Would you like to make another transaction?");
			userAnswer = keyboard.nextLine();
		}
		
		//If the user said "no"
		if(userAnswer.equalsIgnoreCase("no")){
			System.out.println("Thank you for using Heel Banking! Goodbye.");
		}
		else{
			System.out.println("Invalid Response.");
			System.out.println("Thank you for using Heel Banking! Goodbye.");
		}
	
	}
}
