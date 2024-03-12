## Аюпов Евгений 
### Задание 1
 -   Скриншот-1 к заданию 1: [Статус Выполнения job_](https://github.com/Ruin392/sdvps-materials/assets/53511812/71c855ba-1660-4a96-9fed-d08beaf6b9e0)

 -   Скриншот-2 к заданию 1: [Статус Выполнения job_2](https://github.com/Ruin392/sdvps-materials/assets/53511812/0019e959-befb-4fcf-ad13-3c3b5ff4d6fb)
 -   Скриншот- 3 к заданию 1: [Настройка Job](https://github.com/Ruin392/sdvps-materials/assets/53511812/b87f0d74-8afb-41d7-84b5-21b4593d0777)



### Задание 2
- Скриншот-1 к заданию 2 : [Сборка](https://github.com/Ruin392/sdvps-materials/assets/53511812/3ce87437-c6f2-4eeb-86cd-2007ea9945a5)

- Код с измененными конфигами (указал абсолютные пути )
```
pipeline {
 agent any
 stages {
  stage('Git') {
   steps {
       sh 'cd /var/lib/jenkins/workspace/Pipe-HW'
       git 'https://github.com/netology-code/sdvps-materials.git'
       
   }
  }
  stage('Test') {
   steps {
    sh 'cd /var/lib/jenkins/workspace/Pipe-HW '
    sh 'go test .'
   }
  }
  stage('Build') {
   steps {
    sh 'cd /var/lib/jenkins/workspace/Pipe-HW'
    sh 'docker build . -t ubuntu-bionic:8082/hello-world:v$BUILD_NUMBER'
   }
  }
  stage('Push') {
   steps {
    sh 'cd /var/lib/jenkins/workspace/Pipe-HW'
    sh 'docker login ubuntu-bionic:8082 -u admin -p R0g3yufuty && docker push ubuntu-bionic:8082/hello-world:v$BUILD_NUMBER && docker logout'   }
  }
 }
}
```
### Задание 3
- Скриншот-1 задание 3 : [Статус сборки](https://github.com/Ruin392/sdvps-materials/assets/53511812/e31c3562-ea62-449a-8987-c361ff498624)
- Код pipeline 
```
pipeline {
 agent any
 stages {
  stage('Build') {
   steps {
    sh 'cd /var/lib/jenkins/workspace/Create-go-bin/'   
    sh 'CGO_ENABLED=0 GOOS=linux /usr/local/go/bin/go build -a -installsuffix nocgo -o sdvps-materials'
   }
  }
  stage('PUT') {
    steps {
      sh 'cd /var/lib/jenkins/workspace/Create-go-bin/'
      sh 'curl -X PUT   -u admin:R0g3yufuty  -H "Content-Type: application/octet-stream"   -F "file=@sdvps-materials"   "http://localhost:8081/repository/my-raw/sdvps-materials"'
    }
  }
 }
}

```
- Скриншот-3 задание 3 : [Файл на сонар кьюбе ](https://github.com/Ruin392/sdvps-materials/assets/53511812/67a1a316-9c52-4cd9-87f9-969df37f0127)





