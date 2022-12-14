# Домашнее задание к занятию "11.04 Микросервисы: масштабирование"

Вы работаете в крупной компанию, которая строит систему на основе микросервисной архитектуры.
Вам как DevOps специалисту необходимо выдвинуть предложение по организации инфраструктуры, для разработки и эксплуатации.

## Задача 1: Кластеризация

Предложите решение для обеспечения развертывания, запуска и управления приложениями.
Решение может состоять из одного или нескольких программных продуктов и должно описывать способы и принципы их взаимодействия.

Решение должно соответствовать следующим требованиям:
- Поддержка контейнеров;
- Обеспечивать обнаружение сервисов и маршрутизацию запросов;
- Обеспечивать возможность горизонтального масштабирования;
- Обеспечивать возможность автоматического масштабирования;
- Обеспечивать явное разделение ресурсов доступных извне и внутри системы;
- Обеспечивать возможность конфигурировать приложения с помощью переменных среды, в том числе с возможностью безопасного хранения чувствительных данных таких как пароли, ключи доступа, ключи шифрования и т.п.

Обоснуйте свой выбор.

### Ответ: 

В части ответа на данный вопрос, я буду опираться на информацию, которую нашел на просторах Интернета.

Скорее всего, это будет Kubernetes (k8s) - лично с ним не работал еще. Но по информации из официального источника "https://kubernetes.io/ru/docs/home/" можно сделать вывод, что он как раз подходит под все наши задачи, а именно создан для оркестрации контеризованными приложениями. 

Обеспечивает маршрутизацию, развертывание и управление данными приложениями. 

Обеспечивает разделение ресурсов, за счет использования пространства имен и настройки взамиодействия между кластерами k8s. 

Позволяет автоматически масштабировать свою архитектуру (по заверениям производителя: обладает ***масштабируемостью любого уровня***).

Позволяет работать с независимыми пространствами имен (https://kubernetes.io/ru/docs/concepts/overview/working-with-objects/namespaces/), что даёт нам возможность безопасного хранения чувствительных данных. 

Kubernetes может быть развернут как в облаке, так и локально, что так же дает преимущество организациями для выбора управления архитектурой и модели постраения взаимодействия между сервисами.

Как аналог, который можно противопоставить k8s можно выбрать Docker, а точнее Docker Swarm. (нашел статью со сравнительным анализом обоих данных продуктов https://mcs.mail.ru/blog/docker-swarm-ili-kubernetes-chto-luchshe). Правда необходимо отметить, что в случае Docker Swarm у нас не будет выполняться условие автоматического масштабирования, его сложно реализовать в Docker Swarm, придется много чего дорабатывать, в отличии от k8s. Но в остальном он нам бы подошел, Docker так же строит свою виртуальную сеть, маршрутизирует информацию между контейнерами, управляет ими.

Но для решения наших задач, должны выполняться все условия, по этому, будем работать с k8s.

Правда необходимо отметить, что во многих источниках, которые я встречал в интернете, утверждается, намекается, подчеркивается, что работа с k8s требует определенных навыков. Другими словами - он не для новичков в данном направлении и потребуется время для его изучения.
