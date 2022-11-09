# Brewscope

## Author/maintainer

- Carl Sandberg
- Contact: [visualarea.1@gmail.com](visualarea.1@gmail.com)

## Description 

Technica
The goal

A small application that utilizes the 
[Punk API](https://punkapi.com/documentation/v2) to display craft beers
and various related information for users.

## Usage

- Clone this repository
- Connect to the docker container in a VS Code Remote Containers environment
- Navigate to the "brewscope" application folder.
- Launch the server with the "rails server" command.
- Navigate to [http://localhost:3000](http://localhost:3000)

## Task analysis

In order to make the application light weight and portable all database 
dependent design options were dropped in favor of a thin client based approach
that relies on the [JavaScript Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)
to retrieve the relevant data, which is then post-processed in various ways 
to make it presentable for the end user.

## Approach description

The client is based on a rails scaffolding, making the application simple to extend
in most ways (integration of databases, routing expansion, middleware design and more)
The Javascript implementation is designed to be kept modular and extensible by 
clear segementation of functionality and structures (modules, types).

## Application testing

The application was tested by implementing proper try catch error handling in all 
relevant sequences of the code (mainly the API fetch sequences). 
Anything above this was considered too elaborate in relation to the simplicity 
of the project. Furthermore, all 'GET' requests are redirected to the relevant 
"/beers" page and all 'POST' requests are denied via a custom route guard in the
ruby routing config.

## Addendums

A more fully featured (MVC) application was initially intended, but since
the API is accessed via REST, the solution was considered too cumbersome for the 
project. Instead, the application (with the effect of the applied routing solution)
is essentially an SPA. The rails scaffolding was kept intact, with a simple "Beer" 
Model migrated to the postgres database for potential use if wanted (accessible in REPL
via the "rails console" command).
