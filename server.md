import socket
import sqlite3


db = sqlite3.connect()
cursor1 = db.cursor()
cursor1.execute("CREATE TABLE if not exists login_info(name TEXT NOT NULL , email TEXT NOT NULL, address TEXT NOT NULL , username TEXT PRIMARY KEY NOT NULL, password TEXT NOT NULL)")


cursor1.execute("CREATE TABLE if not exists product_info(username TEXT PRIMARY KEY NOT NULL ,name TEXT NOT NULL, picture BLOB NOT NULL , price REAL NOT NULL, description TEXT NOT NULL)")
db.commit()



server_domain = '127.0.0.1'
server_port = 8080
server_socket = socket.socket(socket.AF_INET , socket.SOCK_STREAM)
server_socket.bind((server_domain, server_port))

server_socket.listen(5)
print(f"Server is operating on {server_domain} : {server_port}")

while True :
    client_socket , client_address = server_socket.accept()
    print(f"Connection from {client_address}")
