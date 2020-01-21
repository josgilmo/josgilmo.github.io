---
layout: post
title: Sincurrencia en go
---

Reglas para el dueño de un channel. 

1. Instantiate the channel.
2. Perform writes, or pass ownership to another goroutine.
3. Close the channel.
4. Ecapsulate the previous three things in this list and expose them via a reader channel.


# Quiz 1
## Question 1
Qué devuelve esto? (Deadlocks).
https://play.golang.org/p/iTAKQmZkDbl

## Question 2
Qué devuelve esto (reading from a closed channel):
https://play.golang.org/p/JA_l0s2bhY6

## Question 2
Qué devuelve esto? (nil channels).
https://play.golang.org/p/1dJNpdbOMpp

## Question 3
Qué devuelve esto (closing nil channel):
https://play.golang.org/p/7GGPRwwg2z5


## Question 5
Qué devuelve esto:
https://play.golang.org/p/Q0FvgrY9scC


# Quiz 2:
## Question 1.

stringStream := make(chan string) go func() {
        close(stringStream)
    }()
    salutation, ok := <-stringStream
    fmt.Printf("(%v): %v", ok, salutation)
}



https://play.golang.org/p/vVhLTD5zaKO

that is the value for "ok"?




## Question 2
https://play.golang.org/p/D0u_I3KWqMw

## Question 3
Buscar un escenario de bloqueo en escritura para channels buffered.
https://play.golang.org/p/OgxbFbyvoXt




## Question 9:
sincronización de timings.
https://play.golang.org/p/GSS4bgJMSw4

## Question 10:
https://play.golang.org/p/Hh97uPWIqHi

# Patterns in Go
## or Pattern:
https://play.golang.org/p/ppyAH-_0prJ

## OrDone Pattern:
https://play.golang.org/p/2tKo4ut3MSP

## tee Pattern:
https://play.golang.org/p/bFm16a4UYjm



