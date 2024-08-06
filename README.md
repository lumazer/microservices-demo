# Репозиторий приложения с pipeline OTUS Kuber-2024-02
## URL до ресурсов
URL тестового контура - https://online-boutique.lunohod-07.ru/
URL Argo CD - https://argocd.lunohod-07.ru/
  - логин admin
  - пароль FUBmY5kB1eSQoY80
URL Prometheus - https://prometheus.lunohod-07.ru/
URL Grafana - https://grafana.lunohod-07.ru/
  - логин admin
  - пароль prom-operator

GITHUB с манифестами и разворачиванием кластера - https://github.com/lumazer/kubernetes_cluster/tree/main
GITHUB с приложением и демонстрацией pipeline - https://github.com/lumazer/microservices-demo/tree/main

## Тестовый контур
На тестовый контур приложение разворачивается с помощью Argo CD используя yaml - https://github.com/lumazer/kubernetes_cluster/blob/main/application-online-boutique.yaml
## Продуктивный контур
На продуктивный контур приложение разворачивается с помощью github actions - [https://github.com/lumazer/kubernetes_cluster/blob/main/application-online-boutique.yaml](https://github.com/lumazer/microservices-demo/edit/main/.github/workflows/blank.yml)
URL продуктивного контура - [https://online-boutique.lunohod-07.ru/](https://online-boutique-prod.lunohod-07.ru/)

# Описание pipeline
1. Удаляем тестовый namespace online-boutique
2. Ждём, пока Argo CD поднимет все ресурсы тестового контура с помощью self-heal
3. Проверяем на наличие фразы "demo purposes only" минимум дважды в front
4. Проводим smoke тест используя встроенное приложение loadgenerator
5. Запускаем приложение online-boutique-prod используя kubectl в github actions
