# distributex

## 🚧 WIP 🚧 - This is very much a work-in-progress project

This is a POC of a federated application combining the Xs of NGINX and HTMX

## Architecture

![Architecture](/architecture.png?raw=true "architecture diagram")

## Tech stack

 - Main app: HTMX, NGINX, and Tailwind
 - Docker 
 - Service 1 (Todo list) - Golang & Sqlite
 - Service 2 (Chat) - Rust & Websockets
 - Service 3 (Tech News) - Python & Hackernews API

## Why?

Why not? Plus I wanted to understand how much I can stretch the idea.

## Main goals

As a dev, you should be able to do/have:

 - A DX & UX isolation, which means accessing the service URL gives you the same UX as in the main APP.
 - Freedom of choice, it shouldn't matter the stack you pick for the services as long you respect the protocol
 - Communication via events

## Current state

 - [x] Main app
   - [x] Serve index.html 
   - [x] Proxy requests to services
 - [x] Todo service
   - [x] Add item
   - [x] Remove item
   - [x] Mark as done
   - [ ] Make it reactive to changes from other sessions (websocket?)
 - [x] Chat service 
   - [x] Allow pick nickname
   - [x] Join a room
   - [x] Send and receive messages
 - [x] News service
   - [x] Allow fetch latest news
   - [x] Allow managing favorite news
 - [x] Main app serving widgets
   - [x] Todo service
   - [x] Chat service
   - [x] News service
   - [ ] Fallback for service loading
 - [x] Implement the 3rd service 
 - [ ] Communication between widgets?

## Getting started

### Requirements

Make sure you have 
 - [docker](https://docs.docker.com/engine/install/)
 - [docker compose](https://docs.docker.com/compose/install/)

If you are on OSX we recommend installing [colima](https://github.com/abiosoft/colima) as a container runtime

### Running

```bash
make start
```

That's it, you should be able to access the main application at http://localhost:4040

You also should be able to access the microservices at:
  - Todo list manager - http://localhost:4001/todo
  - Chat service - http://localhost:4002/chat
  - Tech News reader - http://localhost:4003/news

### Live reload mode

You need [funzzy](https://github.com/cristianoliveira/funzzy) (sorry?)

First, start the services with `make start` then in another terminal do:

```bash
make watch
```
