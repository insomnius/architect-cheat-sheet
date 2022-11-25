# What is this about?

I put all notes from my experience as a software engineer here, to remind me about a problem that I face previously.

## Google Pubsub

- Always consider to increase ack deadline when it comes to high processing time background job
  - The default ack deadline of pubsub is 10 seconds, the maximum is 600 seconds (10 minutes) https://cloud.google.com/pubsub/docs/reference/rest/v1/projects.subscriptions/modifyAckDeadline
  - Consider using republish logic for jobs that run more than 10 minutes


## Kafka

- Always consider session timeout when it comes to high processing time background job

## HTTP

- About TCP TIME_WAIT state
  - Always close http connection, if no then it would create too much TCP with TIME_WAIT state which may affect your service performances. Read: http://projectsweb.cs.washington.edu/research/projects/networking/www/detour/local/infocom99/papers/11b_04.pdf
  - Always use persistent HTTP, in order to reuse the current established TCP connection instead of creating a new one. Reference: http://tleyden.github.io/blog/2016/11/21/tuning-the-go-http-client-library-for-load-testing/

## Consistency

- In event driven architecture, you must choose only one consistency whether it is the message broker or the database that should be consistent.