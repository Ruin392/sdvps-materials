## Аюпов Евгений 
### Задание 1
 -   Скриншот-1 к заданию 1: 

[Статус Выполнения job](https://github.com/Ruin392/sdvps-materials/assets/53511812/f2b803e9-60cb-43f8-a2d6-32b8db0aed11)
 -   Скриншот-2 к заданию 1: 
 [Статус Выполнения job](https://github.com/Ruin392/sdvps-materials/assets/53511812/0019e959-befb-4fcf-ad13-3c3b5ff4d6fb)
-   Скриншот- 3 к заданию 1:
-   
 ![image](https://github.com/Ruin392/sdvps-materials/assets/53511812/c195c86a-ba7c-4b33-a95a-03255ac57ad0)


### Задание 2
- Скриншот-1 к заданию 2
 ![image](https://github.com/Ruin392/sdvps-materials/assets/53511812/3ce87437-c6f2-4eeb-86cd-2007ea9945a5)

- Код с измененными конфигами (указал абсолютные пути )
```
pipeline {
 agent any
 stages {
  stage('Git') {
   steps {git 'https://github.com/netology-code/sdvps-materials.git'}
  }
  stage('Test') {
   steps {
    sh 'cd /var/lib/jenkins/workspace/Net-Pipe'
    sh '/usr/local/go/bin/go test .'
   }
  }
  stage('Build') {
   steps {
    sh ' /usr/bin/docker build . -t ubuntu-bionic:8082/hello-world:v$BUILD_NUMBER'
   }
  }
 }
}
```

