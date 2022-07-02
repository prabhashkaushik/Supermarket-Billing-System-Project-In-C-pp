#include<iostream>
#include<fstream>


using namespace std;
 
 class shopping
 {
 	private:
 		int pcode;
 		float price;
 		float dis;
 		string pname;
 		
 		public:
 			void menu();
 			void administrator();
 			void buyer();
 			void add();
 			void edit();
 			void rem();
 			void list();
 			void receipt();
 			
 };
 
 void shopping :: menu()
 {
 	m:
 	int choice;
 	string email;
 	string password;
 	
 	cout<<" \t\t\t\t.....................................\n";
 	cout<<" \t\t\t\t                                     \n";
 	cout<<" \t\t\t\t        Supermarket Main menu        \n";
 	cout<<" \t\t\t\t                                     \n";
 	cout<<" \t\t\t\t.....................................\n";
 	cout<<" \t\t\t\t                                     \n";
 	cout<<" \t\t\t\t   1) Administrator        |\n";
 	cout<<" \t\t\t\t                           |\n";
 	cout<<" \t\t\t\t   2) Buyer                |\n";
 	cout<<" \t\t\t\t                           |\n";
 	cout<<" \t\t\t\t   3) Exit                 |\n";
 	cout<<" \t\t\t\t                           |\n";
 	cout<<" \n\t\t\t  please select! ";
 	cin>> choice;
 	
 	switch(choice)
 	{
 		case 1:
 			cout<<"\t\t\t please login \n";
 			cout<<"\t\t\t Enter email \n";
 			cin>> email;
 			cout<<"\t\t\t password \n";
 			cin>>password;
 			
 			if(email=="prabhashkaushik123@gmail.com" && password== "8447421306")
 			{
 				administrator();
			 }
			 else
			 {
			 	cout<<"Invalid email/password";
			 }
			 break;
		
	 
	 case 2:
	 {
	 	buyer();
	 }
	 case 3:
	 	{
	 		exit(0);
		 }
		 default :
		 	{
		 		cout<<"Please se;ect from the given options:";
			 }
}
 goto m;
}
void shopping::administrator()
{
	m:
	int choice;
	cout<<"\n\n\n\t\t\t administrator menu";
	cout<<"\n\t\t\t|                            ";
	cout<<"\n\t\t\t|____1)Add the product_______";
	cout<<"\n\t\t\t|                            ";
	cout<<"\n\t\t\t|____1)Modify the product____";
	cout<<"\n\t\t\t|                            ";
	cout<<"\n\t\t\t|____1)Delete the product____";
	cout<<"\n\t\t\t|                            ";
	cout<<"\n\t\t\t|____1)Back to the menu______";

	cout<<"\n\n\t Please enter your choice";
	cin>>choice;
	
	switch(choice){
		case 1:
			add();
			break;
		case 2:	
			edit();
			break;
		case 3:	
			rem();
			break;
		case 4:
			menu()	;
			break;
		default :
			cout<<"Invalid choice!";	
	}
goto m;
}
void shopping:: buyer(){
	m:
	 int choice;
	 cout<<"\t\t\t Buyer \n";
	 cout<<"\t\t\t_______________ \n";
	 cout<<"                      \n";
	 cout<<"\t\t\t1) Buy product  \n";
	 cout<<"                      \n";
	 cout<<"\t\t\t2) Go back      \n";
	 cout<<"\t\t\t Enter your choice : ";
	 cin>>choice;

	 switch(choice){
		case 1:
			receipt();
			break;
		case 2:
			menu();
		default:
			cout<<"invalid choice"	;
	 }
	 goto m;
}

void shopping :: add()
{ 
	m:
	fstream data;
	int c;
	int token=0;
	float p;
	float d;
	string n;

	cout<<"\n\n\t\t\t Add new product";
	cout<<"\n\n\t Product code of the product ";
	cin>>pcode;
	cout<<"\n\n\t Name of the product";
	cin>>pname;
	cout<<"\n\n\t Price of the product";
	cin>>price;
	cout<<"\n\n\t Discount on product";
	cin>>dis;

	data.open("database.txt",ios::in);

	if(!data){
		data.open("database.text",ios::app|ios::out);
		data<<" "<<pcode<<" "<<pname<<" "<<price<<" " <<dis<<"\n";
		data.close();
	}
	else{
		data>>c>>n>>p>>d;
		while(!data.eof()){
			if(c==pcode){
				token++;
			}
			data>>c>>n>>p>>d;
		}
		data.close();
	
	if(token==1){
		goto m;
	}
	else{
	data.open("database.text",ios::app|ios::out);
		data<<" "<<pcode<<" "<<pname<<" "<<price<<" " <<dis<<"\n";
		data.close();
	}
}
cout<<"\n\n\t\t Record inserted !";
}


void shopping ::edit()
{
	fstream data,datal;
	int pkey;
	int token=0;
	int c;
	float p;
	float d;
	string n;
	cout<<"\n\t\t\t Modify the record";
	cout<<"\n\t\t\t Product code :";
	cin>>pkey;

	data.open("database.txt",ios::in);
	if(!data){
		cout<<"\n\nFile doesn't exist!";
	}
	else{
		data1.open("database1.text",ios::app| ios::out);

		data>>pcode>>pname>>price>>dis;
		while(!data.eof()){
			if(pkey==pcode){
				cout<<"\n\t\t Product new code :";
				cin>>c;
				cout<<"\n\t\t Name of the product: ";
				cin>>n;
				cout<<"\n\t\t Price :";
				cout<<"\n\t\t Discount :";
				cin>>d;
				data1<<" "<<c<<" "<<n<<" "<<p<<" "<<d<<"\n";
				cout<<"\n\n\t\t Record edited ";
				token++;
			}
			else{
				data1<<" "<<pcode<<" "<<pname<<" "<<price<<" "<<dis<<"\n";
			}
			data>>pcode>>pname>>price>>dis;
		
	}
	data.close();
	data1.close();
	remove("database.txt");
	rename("database1.txt","database.txt");

	if(token==0){
		cout<<"\n\n Record not found sorry!";
	}
}
	}

	void shopping ::rem(){
		fstream data ,data1;
		int pkey;
		int token=0;
		cout<<"\n\n\t Delete product";
		cout<<"\n\n\t product code :";
		cin>>pkey;
		data.open("dayabase.txt"mios::in);
		if(!data){
			cout<<"File doesn't exist";
		}
		else{
			data1.open("database1.txt",ios::app|ios::out);
			data>>pcode>>pname>>price>>dis;
			while(!data.eof()){
				if(pcode==key){
					cout<<"\n\n\t product delete succesfully";
					token++;
				}
				else{
					detail<<" "pcode<<" "<<pname<<" "<<price" "<<dis<<"\n";
				}
				data>>pcode>>pname>>price>>dis;
			}
			data.close();
			data1.close();
			remove("database.txt");
			renmae("database1.txt","database.txt");

			if(token==0){
				cout<<"\n\n Record not found";
			}
		}
	}

	void shopping:: list()
	{
		fstream data;
		data.open("database.txt",ios::in);
		cout<<"\n\n|_________________________________________________\n";
		cout<<"ProNo\t\tName\t\tPrice\n";
		cout<<"\n\n|_________________________________________________\n";
		data>>pcode>>pname>>price>>dis;
		while(!data.eof()){
			cout<<pcode<<"\t\t"<<pname<<"\t\t"<<price<<"\n";
			data>>pcode>>pname>>price>>dis;

		}
		data.close();
	}
	void shopping receipt()
	{
		fstream data;
		int arrc[100];
		int arrq[100];
		char choice;
		int c=0;
		float amount=0;
		float dis=0;
		float total=0;

		cout<<"\n\n\t\t\t\t RECEIPT" ;
		data.open("data.txt", ios::in);
		if(!data){
			cout<<"\n\n Empty database";

		}
		else{
			data.cloase())

			list();
			cout<<"\n____________________________\n";
			cout<<"\n|___________________________\n";
			cout<<"\n  please place the order    \n";
			cout<<"\n____________________________\n";
			cout<<"\n|___________________________\n";
			do{
				m:
				cout<<"\n\n Enter product code :";
				cin>>arrc[c];
				cout<<"\n\n Enter the product qiantity :";
				cin>>arrq[c];
				for(int i=0;i<c;i++){
					if(arrc[c]==arrc[i])
					{
						cout<<"\n\n Duplicate product code. PLease try again!";
						goto m;
					}
				}
				c++;
				cout<<"\n\n Do you want to buy another product? if yes then press y else no";
				cin>>choice;

			}
			while(choice=="y"){

				cout<<"\n\n\t\t\t______________________RECIEPT_______________\n";
				cout<<"\nProduxt No\t Product Name\t product quantity\tPrice\taAmount with discount\n";

				for(int i=0;i<c;i++){
					data.open("database.txt",ios::in);
					data>>pcode>>pname>>price>>dis;
					while(!data.eof()){
						if(pcode==arrc[i]){
							amount=price*arrq[i];
							dis=amount-(amount*dis/100);
							total=total+dis;
							cout<<"\n"<<pcode<<"\t\t"<<pname<<"\t\t"<<arrq[i]<<"\t\t"<<price<<"\t"<<amount<<"\t\t"<<dis;
						}
						data>>pcode>>pname>>price>>dis;
					}
				}
				data.close();

			}
			cout<<"\n\n________________________________________";
			cout<<"\n Total Amount : "<<total;
		}
	}

int main(){
	shopping s;
	s.menu();
}
