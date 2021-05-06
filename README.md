# Lab2
Lab2 PPK OOP

# Приклад роботи програми:
<img src="https://i.ibb.co/5Ly2JH3/image.png" alt="image" border="0">

## Нова команда "report":
```java
else if("report".equals(line)){
                System.out.println("\nCUSTOMERS REPORT");
                System.out.println("================");

                for(int cust_idx = 0; cust_idx < Bank.getNumberOfCustomers(); ++cust_idx) {
                    Customer customer = Bank.getCustomer(cust_idx);
                    System.out.println();
                    System.out.println("Customer: " + customer.getLastName() + ", " + customer.getFirstName());

                    for(int acct_idx = 0; acct_idx < customer.getNumberOfAccounts(); ++acct_idx) {
                        Account account = customer.getAccount(acct_idx);
                        String account_type = "";
                        if (account instanceof SavingsAccount) {
                            account_type = "Savings Account";
                        } else if (account instanceof CheckingAccount) {
                            account_type = "Checking Account";
                        } else {
                            account_type = "Unknown Account Type";
                        }

                        System.out.println("    " + account_type + ": current balance is " + account.getBalance());
                    }
                }
            }
