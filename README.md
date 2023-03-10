# COMP 3010 Distributed Computing
### 3010MQ
![](./doc/A1.png)
_Producer_ 
- Sends jobs to the broker and gets a job ID as a response for each job successfully stored
- Asks for the status of a job with the specified ID

_Broker_
- Maintains a FIFO queue to store the jobs sent from the client
- Sends jobs each to a single worker upon polling
- Sends job status to the client upon requesting

_Consumer_
- Polls jobs from the broker and send the texts one word at a time to a user-defined UDP port
- Logs progress while handling a job to another user-defined UDP port
- Notifies the broker upon job completion
- Reconnects to the broker if disconnected with retry per second
