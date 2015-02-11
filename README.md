## Content Description
The execution of the server follows four steps:

1.	Create a socket for the server
2.	Bind that socket to an address
3.	Listen for connections and accept them
4.	Read the incoming message, create a string that repeats the message three times and then send the modified response back.

## The concurrency of the server
This server uses process concurrency. Process concurrency is not the most efficient concurrency as process creation is an expensive task for the OS and CPU. To mitigate this problem, the listen function does not allow any backlog requests so all processes are short. In a real world situation this does result in more drops but in this case, each terminal does not issue that many requests each and each process can be executed and finished relatively quickly. While process creation is more expensive, it does not suffer from race conditions like concurrent threading does.

## Execution of process concurrency
1.	Fork and check if fork was successfully.
2.	The child process will execute the new client request
3.	The parent process will close the received client and wait for another client and create another child when the next client connects.

