#!groovy

properties properties: [
    disableConcurrentBuilds(),
    [$class: 'BuildDiscarderProperty', strategy:
        [$class: 'LogRotator', artifactDaysToKeepStr: '7', artifactNumToKeepStr: '10', daysToKeepStr: '7', numToKeepStr: '10']
    ]
]

final languages = [
    "C/C++": [tag: "lang-cpp:7.3.0", dockerfile: "Dockerfile-cpp"],
    "Java": [tag: "lang-java:8-jdk-alpine", dockerfile: "Dockerfile-java"],
    "Scala": [tag: "lang-scala:2.13.4-alpine", dockerfile: "Dockerfile-scala"],
    "Kotlin": [tag: "lang-kotlin:1.4.20-alpine", dockerfile: "Dockerfile-kotlin"],
    "NodeJs": [tag: "lang-node:14.15.1-alpine", dockerfile: "Dockerfile-node"],
    "Python": [tag: "lang-python:3.6.1-alpine", dockerfile: "Dockerfile-python"]

]

node("main") {
    stage("Checkout") {
        checkout scm
    }

    def image
    def language = languages[env.LANG]

    stage("Build ${env.LANG} Image") {
        image = docker.build("tunjudge/${language.tag}", "-f docker/${language.dockerfile} .")
    }

    docker.withRegistry('', 'docker') {
        stage("Publish ${env.LANG} Image") {
            image.push()
        }
    }
}
