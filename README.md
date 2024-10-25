import socket
import sqlite3


user_database = sqlite3.connect()
cursor1 = user_database.cursor()
cursor1.execute("CREATE TABLE login_info(name , email , address , username , password)")
user_database.commit()

product_database =sqlite3.connect()
cursor2 = product_database.cursor()
cursor2.execute("CREATE TABLE product_info(name , picture , price , description )")




server_domain = '127.0.0.1'
server_port = 8080
server_socket = socket.socket(socket.AF_INET , socket.SOCK_STREAM)
server_socket.bind((server_domain , server_port))

server_socket.listen(5)
print(f"Server is operating on {server_domain} : {server_port}")

while true :
    client_socket , client_address = server_socket.accept()
    print(f"Connection from {client_address}")
