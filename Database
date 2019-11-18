import datetime
import sqlite3

conn = sqlite3.connect('complaint.db')
c = conn.cursor()


class Customer():

    def __intit__(self, complaint, name, address):
        self.complaint = complaint
        self.name = name
        self.address = address

    def inputing(self):
        
        name = input("Enter your name:")
        complaint = input("Enter your complaint:")
        address = input("Enter your address:")
        self.name=name
        self.complaint= complaint
        self.address = address

#This should be run only in the start of the project
#The command is to CREATE a table of the following instances
'''c.execute("""CREATE TABLE complaint (
            date DATE,
            name text,
            complaint text,   
            address text)""")'''


def enter():
    cus = Customer()
    cus.inputing()
    c.execute(f"INSERT INTO  complaint VALUES ('{cus.name}', '{cus.complaint}','{cus.address}')")
    conn.commit()


def delete_this(del_name):
    c.execute(f"DELETE FROM complaint WHERE name='{del_name}'")


def view(view_name):
    if view_name=="*":
        c.execute(f"SELECT * FROM complaint")
    else:
        c.execute(f"SELECT * FROM complaint WHERE {view_name}")


###________________________________________________________________________________________________________________###

# MAIN
def main():
    ch="y"

    while ch.islower()=="y" and ch.islower()=="yes":
        print("press 1 for adding new customer details \npress 2 for deleting a customer details \npress 3 for viewing table")
        option = int(input())

        if option==1:
            enter()

        elif option == 2:
            print("enter the name of the person whose name should be deleted:")
            del_name = input()
            delete_this(del_name)

        elif option == 3:
            print("to view the whole table press * , for particular table view enter name:")
            view_name = input()
            view(view_name)

        else:
            print("invalid choice")

        ch=input("continue working :")




#Formalities
print(c.fetchall())
conn.commit()
conn.close()
