#!/usr/bin/groovy


def somevar
def buildEnv = ["ABC=123"]

node {

  def scmVarMap = checkout scm
  scmVarMap.each { buildEnv.push("${it.key}=${it.value}") }

  withEnv(buildEnv) {
    stage("First stage") {
      somevar = 1234
      echo "first stage, set somevar, somevar: ${somevar}"
      sh "env"
    }

    stage("Second stage") {
      echo "second stage, somevar: ${somevar}"
      sh "env"
    }
  }

  stash "Jenkinsfile", name: "Jenkinsfile"

}

input "flyweight step, continue?"

node {
  unstash "Jenkinsfile"

  withEnv(buildEnv) {
    stage("Third stage") {
      echo "third stage, somevar: ${somevar}"
      sh "env"
    }

    stage("Final stage") {
      echo "final stage, somevar: ${somevar}"
      sh "env"
    }
  }

}