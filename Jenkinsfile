#!/usr/bin/groovy

node {

  def somevar = "somevariable"

  stage("First stage") {
    echo "first stage, somevar: ${somevar}"
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