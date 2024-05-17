# Lab grpc in Go

This is a toy project to experiment with grpc and go (context especially).
I'm learning, so don't take this code too seriously!

# Definition of Done

I'll be done with this project when this list of todos will be completed:

- [] 2 microservices
  - [] 1 grpc server
  - [] 1 grpc client with http endpoints to interact with the system
- [] docker compose
- [] use of goroutines for parallel execution
- [] use of context to cancel long requests
- [] use of lock in grpc server to simulate request using unique resource


# Architecture

One microservice (A) serves an http server publicly available.
Another (B) serves gRPC endpoints, available only for the first service A.

gRPC requests should take less than 100ms to get responses.

The service B has a lock on one method so multiple goroutines have to wait for their turn.
The method takes 70ms to return, so one request can be handle but with 2 requests, the second one should timeout.

# Experiment

Run client/server apps with gRPC and go.

Send 2 requests to see the cancel context in action, with the lock.
