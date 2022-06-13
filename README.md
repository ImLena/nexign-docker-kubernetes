# Сборка веб-приложения в виде Doker image и установка в кластер Kubernetes

Создание image:   
*docker build -t imlena/web:1.0.0 .*  
      
Запуск контейнера для проверки работы приложения:  
*docker run -it -p 8000:8000 --name=web <image_id>*  
  
Загрузка image на DockerHub:  
*docker push imlena/web:1.0.0*  
  
Для удобства новый кластер Kubernetes создадим с помощью minikube:  
*minikube start*  
  
Установка manifest в кластер Kubernetes:  
*kubectl apply -f manifest.yaml*  
  
Чтобы обеспечить доступ к web-приложению внутри кластера пробросим порт:  
*kubectl port-forward --address 0.0.0.0 pod/web 8080:8000*  
  
Теперь веб-приложение доступно локально по адресу http://127.0.0.1:8080/hello_docker.html
