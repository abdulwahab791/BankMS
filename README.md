#include<iostream>
#include<fstream>
#include<string>
#include<vector>
#define RED     "\033[31m"
#define GREEN   "\033[32m"
#define YELLOW  "\033[33m"
#define BLUE    "\033[34m"
#define SILVER  "\033[37m"
#define WHITE   "\033[00m"
using namespace std;
class question{
    public:
    void tell(){
        string ans;
        cout<<RED<<"Do you have Already account "<<endl;
        cin>>ans;
        if(ans!="yes"){
            cout<<YELLOW<<"OK Don't Worry Let's Create new account "<<endl;
            int DOB;
            long phone_num;
            string name;
            double amt;
            int pin;
            cout<<BLUE"Enter you name :";
            cin>>name;
            cout<<BLUE<<"Enter phone number :";
            cin>>phone_num;
            cout<<BLUE<<"Enter your Date of birth :";
            cin>>DOB;
            cout<<BLUE<<"Create you pin"<<endl;
            cin>>pin;
            cout<<BLUE<<"Enter you Amount "<<endl;
            cin>>amt;
            cout<<BLUE<<"Check you detail "<<endl;
            cout<<name<<endl;
            cout<<phone_num<<endl;
            cout<<pin<<endl;
            cout<<DOB<<endl;
            cout<<amt<<endl;
            string reply;
            cout<<RED<<"You detail is right or not answer in(yes/no)"<<endl;
            cin>>reply;
            if(reply=="yes"){
                ofstream file("accounts.txt");
                file<<pin<<" "<<name<<" "<<amt<<endl;
                file.close();
                cout<<"Your account is created successfully "<<endl;
                cout<<"After 24 hour process you will recive mail from bank"<<endl;
            }
            else{
                cout<<"re-enter plz"<<endl;
            }
        }
        else if(ans=="yes"){
            cout<<GREEN<<"GO to Login......"<<endl;
        }
    }
};
class Account {
public:
    int pin;
    string name;
    double balance;
    void showMenu() {
        int choice;
        do {
            cout<<"<======| Welcome "<<name<<" |======>"<<endl;
            cout<<SILVER<<"1. Deposit"<<endl;
            cout<<YELLOW<<"2. Withdraw"<<endl;
            cout<<RED<<"3. Check Balance"<<endl;
            cout<<WHITE<<"4. Logout"<<endl;
            cout<<BLUE<<"Enter choice: ";
            cin >> choice;
            if (choice == 1) {
                double amount;
                cout << "Enter deposit: ";
                cin >> amount;
                balance += amount;
                cout << "New Balance: "<<balance<<endl;
            }
            else if (choice == 2) {
                double amount;
                cout << "Enter withdraw: ";
                cin >> amount;
                if (amount<= balance) {
                    balance -= amount;
                    cout << "Remaining Balance: "<<balance<<endl;
                } else {
                    cout << "Insufficient balance\n";
                }
            }
            else if (choice == 3) {
                cout << "Balance: " <<balance<< endl;
            }

        } while (choice != 4);
    }
};
int main(){
    cout<<RED<<"~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~"<<endl;
    cout<<endl;
    cout<<YELLOW<<"|             o---<||Welcome to AB's Bank||>---o               |"<<endl;
    cout<<endl;
    cout<<RED<<"~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~"<<endl;   
    int options;
        cout<<RED<<"<~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~>"<<endl;
        cout<<GREEN<<"                 1. Create "<<endl;
        cout<<GREEN<<"                 2. Login"<<endl;
        cout<<GREEN<<"                 3. About"<<endl;
        cout<<GREEN<<"                 4. Exit"<<endl;
        cout<<RED<<"<~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~>"<<endl;
        cout<<"We have 4 options "<<endl;
        cin>>options;
        if(options==1){
            question q;
            q.tell();
        }
        else if(options==2){
             int Pin;
    string name;
    cout<<"<=====| LOGIN |=====>"<<endl;
    cout<<"Enter you name"<<endl;
    cin>>name;
    cout<<"Enter PIN: ";
    cin>>Pin;
    Account accounts[5]={
        {2253,"Wahab",200000},
        {4478,"Ali",150000},
        {2587,"Ahmed",100000},
        {1026,"Burhan",150000},
        {1027,"Hassan",17000}
    };
    bool found = false;
    for (int i = 0; i < 5; i++) {
        if (accounts[i].pin == Pin && accounts[i].name==name) {
            cout << "Login Successful!\n";
            accounts[i].showMenu();     
            found = true;
            break;
        }
    }
      ifstream file("accounts.txt",ios::app);

    Account acc;
        while(file>>acc.pin>>acc.name>>acc.balance){
        if(acc.pin==Pin && acc.name==name){
            cout << "Login Successful!\n";
            acc.showMenu();
            found = true;
            break;
        }
    }

    file.close();

    if (!found) {

        cout << "Account not found!\n";
}
}
else if(options==3){
cout<<"<============= ABOUT SYSTEM =============>"<<endl;
cout<<"Welcome to our Bank Management System"<<endl;
cout<<"This system is developed in C++ using OOP concepts."<<endl;
cout<<"It allows multiple users to create accounts and login securely."<<endl;

cout<<"\nKey Advantages:"<<endl;
cout<<"- Secure login using PIN authentication"<<endl;
cout<<"- Fast and easy account access"<<endl;
cout<<"- Real-time balance updates"<<endl;
cout<<"- Safe deposit and withdrawal system"<<endl;
cout<<"- Transaction tracking for user activity"<<endl;
cout<<"- User-friendly menu interface"<<endl;
cout<<"\nThis project improves programming skills and simulates"<<endl;
cout<<"real-world banking operations."<<endl;
cout<<"<========================================>"<<endl;
string back;
cout<<"write back for reverse "<<endl;
cin>>back;
if(back=="back"){
   cout<<options<<endl;
   main();
}
else{
    cout<<"Error"<<endl;
}
}

else{
    return 0;
}
 int feedback;
    cout<<"<==============================================================>"<<endl;
    cout<<"                 ||FEEDBACK SECTION||"<<endl;
    cout<<"<==============================================================>"<<endl;

    
    cout<<"Enter TRUE Feedback"<<endl;
    cout<<"Select [1 , 2 , 3 , 4 , 5]"<<endl;
    cin>>feedback;
    if(feedback==5){
        cout<<"Very Happy"<<endl;
        cout<<"* * * * *"<<endl;

    }
    else if (feedback==4)
    {
        cout<<"Happy"<<endl;
        cout<<"* * * *"<<endl;
    }
    else if (feedback==3)
    {
        cout<<"Intresting"<<endl;
        cout<<"* * *"<<endl;
    }
    else if (feedback==2)
    {
        cout<<"Fine"<<endl;
        cout<<"* *"<<endl;
    }
    else if (feedback==1)
    {
        cout<<"Bad"<<endl;
        cout<<"*"<<endl;
    }
    else{
        cout<<"Select a right feedback"<<endl;
    }
    cout<<"<==============================================================>"<<endl;
    cout<<"                ||THANK YOU FOR VISITING ||"<<endl;
    cout<<"<==============================================================>"<<endl;
}
