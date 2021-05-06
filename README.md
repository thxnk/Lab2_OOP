# Lab2
Lab2 PPK OOP

# Приклад роботи програми:
<img src="https://i.ibb.co/5Ly2JH3/image.png" alt="image" border="0">

## Метод "ShowCustomerDetails":
```java
private void ShowCustomerDetails() {
        TWindow custWin = addWindow("Customer Window", 2, 1, 40, 10, TWindow.NOZOOMBOX);
        custWin.newStatusBar("Enter valid customer number and press Show...");

        custWin.addLabel("Enter customer number: ", 2, 2);
        TField custNo = custWin.addField(24, 2, 3, false);
        TText details = custWin.addText("Owner Name: \nAccount Type: \nAccount Balance: ", 2, 4, 38, 8);

        DataSource dataSource = new DataSource("C:\\Users\\boss\\Desktop\\TUIdemo\\src\\com\\mybank\\tui\\test.dat");
        try {
            dataSource.loadData();
        } catch (IOException e) {
            e.printStackTrace();
        }
        custWin.addButton("&Show", 28, 2, new TAction() {
            @Override
            public void DO() {
                try {
                    int custNum = Integer.parseInt(custNo.getText());
                    Account account = Bank.getCustomer(custNum).getAccount(0);
                    String account_type = "";
                    if (account instanceof SavingsAccount) {
                        account_type = "Savings Account";
                    } else if (account instanceof CheckingAccount) {
                        account_type = "Checking Account";
                    } else {
                        account_type = "Unknown Account Type";
                    }
                    details.setText("Owner Name: "+Bank.getCustomer(custNum).getFirstName()+ " " + Bank.getCustomer(custNum).getLastName()+" (id="+custNum+")\nAccount Type: '"+account_type+"'\nAccount Balance: $"+account.getBalance());
                } catch (Exception e) {
                    messageBox("Error", "You must provide a valid customer number!").show();
                }
            }
        });
    }
