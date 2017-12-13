#!/usr/bin/groovy


def somevar
def buildEnv = ["ABC=123"]

node('one') {

  def scmVarMap = checkout scm
  scmVarMap.each { buildEnv.push("${it.key}=${it.value}") }

  withEnv(buildEnv) {
    stage("First stage") {
      somevar = 1234
      echo "first stage, set somevar, somevar: ${somevar}"
      sh "env"
      sh "ls -lah"
    }

    stage("Second stage") {
      echo "second stage, somevar: ${somevar}"
      sh "env"
      sh "ls -lah"
    }
  }

  stash includes: "Jenkinsfile", name: "Jenkinsfile"
}

input "flyweight step, continue?"

node('two') {
  checkout scm
  withEnv(buildEnv) {
    stage("Third stage") {
      echo "third stage, somevar: ${somevar}"
      sh "env"
      sh "ls -lah"
    }

    stage("Fourth stage") {
      echo "Fourth stage, somevar: ${somevar}"
      sh "env"
      sh "ls -lah"
    }
  }

}

node('one') {
  checkout scm
  withEnv(buildEnv) {
    stage("Final stage") {
      echo "Final stage, somevar: ${somevar}"
      sh "env"
      sh "ls -lah"
    }
  }
}