README
---------------------

Description
#################
My code works by first creating global variables to keep check of things like buffer size, ports, as well as hashmaps for the connected users, hashmaps that associate users and sockets, sockets and timestamps etc.

The code then checks that the server.py and client.py is called correctly and initializes the USER_PASSWORD credentials. For server.py I then specify helper methods to do the chatroom features like who and last.

Then the server and code starts. The server and client code first has lists for the readable, writeable and error sockets, followed by a try section that encloses the main while loop for both programs (the try accounts for the encounter of any ctrl c).

The server code has two sections enclosed in an infinite loop. The first section authenticates incoming socket connections. It does this through several sections that test if the user has been blocked before, it the username is valid or if the password has been wrong in more than three attempts. Only if all these tests are correct is the user connected. The second section checks for incoming client socket data and issues the appropriate helper methods or commands.

The client server on the other hand, also has an infinite loop with two main sections. One that checks for received data ticket and ticks authenticated as true once the client is welcome to the chat room. The other sends data from the socket to the server and by extension to other users. If the client socket is lost, then the client assumed it was disconnected.

Environment
####################

My code uses Python 2.7.3

Instructions
#####################

run server: python server.py [portname]

run client: python client.py [server IP address or hostname] [server port]

The server only needs to be run as instructed above, it will issue print statements occasionally that I used for debugging and you are free to use to what parts of my code are in action

The client needs to be run as above. Then a username and password prompt will appear, while they have a newline, you should write a correct username and password with no spaces before and after any of these words. These checks do act according to the specifications, so while you can type as many wrong usernames as you want, you only have three chances for a correct password before your ip is blocked.

Once authenticated, a "command: " prompt will appear after typing/sending and receiving information to and from the server respectively, type as you normally would. You can type in all the commands as stated in the spec and below. A client can logout with logout or ctrl c, server can only be terminated through ctrl c.

Sample Commands
#########################

logout:
type: logout

when typing logout, put no spaces before and after, on your terminal.

who:
type: who

when typing who, put no spaces before and after, on your terminal.

last <number>:
type: last <number>

type last, with a space NOT before but after, and then the number of minutes.

broadcast:
type: broadcast <message>

type broadcast, with a space NOT before but after, and then the message.

send to one person:
type: send <user> <message>

type send, with a space NOT before but after, and then the user and message (each with a space in between).

send to many people:
type: send (<user> <user> ... <user>) message

type send, with a space NOT before but after, and then the users enclosed in brackets with spaces between the users but no space in the ones at the start and end of the brackets, and then the message.

