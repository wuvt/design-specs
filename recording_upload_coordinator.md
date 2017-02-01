# Recording Upload Coordinator

We use flint and sultana for recording aircheck and/or pgmcheck. We keep a local buffer to tolerate storage outages, but eventually these recordings need to be moved to permanent storage.

Here's a high-level overview of the logic we came up with:
* liquidsoap submits jobs to the upload coordinator
* upload coordinator keeps track of upload status for a particular job
* upload coordinator pushes into configured upload queues (alexandria and IA)
* when upload coordinator receives a success result for all configured upload queues, the file can be deleted
