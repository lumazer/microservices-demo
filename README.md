# Репоз для проектной работы OTUS Kuber-2024-02
## URL до ресурсов
URL тестового контура - https://online-boutique.lunohod-07.ru/<br>
URL Argo CD - https://argocd.lunohod-07.ru/<br>
  - логин admin<br>
  - пароль FUBmY5kB1eSQoY80<br>
URL Prometheus - https://prometheus.lunohod-07.ru/<br>
URL Grafana - https://grafana.lunohod-07.ru/<br>
  - логин admin<br>
  - пароль prom-operator<br>

GITHUB с манифестами и разворачиванием кластера - https://github.com/lumazer/kubernetes_cluster/tree/main<br>
GITHUB с приложением и демонстрацией pipeline - https://github.com/lumazer/microservices-demo/tree/main

## Тестовый контур
На тестовый контур приложение разворачивается с помощью Argo CD используя yaml - https://github.com/lumazer/kubernetes_cluster/blob/main/application-online-boutique.yaml
## Продуктивный контур
На продуктивный контур приложение разворачивается с помощью github actions - [https://github.com/lumazer/kubernetes_cluster/blob/main/application-online-boutique.yaml](https://github.com/lumazer/microservices-demo/edit/main/.github/workflows/blank.yml)<br>
URL продуктивного контура - [https://online-boutique.lunohod-07.ru/](https://online-boutique-prod.lunohod-07.ru/)

# Описание pipeline
1. Удаляем тестовый namespace online-boutique
2. Ждём, пока Argo CD поднимет все ресурсы тестового контура с помощью self-heal
3. Проверяем на наличие фразы "demo purposes only" минимум дважды в front
4. Проводим smoke тест используя встроенное приложение loadgenerator
5. Запускаем приложение online-boutique-prod используя kubectl в github actions
