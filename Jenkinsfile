#!/usr/bin/groovy


def somevar

node {

  stage("First stage") {
    somevar = 1234
    echo "first stage, set somevar, somevar: ${somevar}"
  }

  stage("Second stage") {
    echo "second stage, somevar: ${somevar}"
  }

}

input "flyweight step, continue?"

node {

  stage("Third stage") {
    echo "third stage, somevar: ${somevar}"
  }

  stage("Final stage") {
    echo "final stage, somevar: ${somevar}"
  }

}