Домашнее задание к занятию 1. «Введение в виртуализацию. Типы и функции гипервизоров. Обзор рынка вендоров и областей применения»
Полная виртуализация эмулирует хост-машину, используя аппаратную поддержку виртуализации на низших уровнях, можно создавать разные ВМ с разными ОС.

При программной виртуализации задействованы отдельные изолированные гостевые ОС, поверх функционирования ОС на хост-машине и прослойки в виде гипервизора

Виртуализация уровня ОС — гипервизор заложен в самой ОС хост-машины, все вм используют одно ядро
Задача 2
* Высоконагруженная база данных, чувствительная к отказу - вероятно, лучше подходит паравиртуализация за счет возможности реализации кластеров и горячей миграции.
* Различные web-приложения - насколько мне известно, для различных веб-сервисов зачастую используют виртуализацию на уровне ОС. Которая обеспечивает упрощенную, понятную отладку за счет использования одного ядра, а также частого использования ОС Linux, имеющего предпочтения у разработчиков.
* Windows системы для использования Бухгалтерским отделом - как и в первом случае, можно сделать выбор в пользу программной виртуализации за счет обеспечения отличной системы резервного хранения и возможности устранения инцидентов без остановки работы за счет горячей миграции.
* Системы, выполняющие высокопроизводительные расчеты на GPU - однозначно физические сервера, т.к виртуализация в любом своем виде будет отнимать ресурсы. На физическом сервере ресурсы можно оптимизировать максимально эффективно для данных задач.
Задача 3
1. Для данной задачи отлично подходят два прямых конкурента MS Hyper-V и VMWare vSphere, обеспечивающие возможность развертывания на данных ОС и поддерживающие отличную отказоустойчивую систему кластеров. С учетом наличия Windows OS, преимущественно можно отдать выбор в сторону Hyper-V за счет отличной совместимости данного гипервизора.
2. KVM или Xen, одни из самых популярных open source решений. Отлично совместимы с указанными ОС и замечательно показывают себя виртуализации небольших инфраструктур
3. Как уже указывал выше, Ms Hyper-v server 2019 отлично подходит в роли гипервизора на базе windows.
4. С учетом отсутствия высоопроизводительных задач и исключительно Linux дистрибутивов, подойдет Oracle VirtualBox или Docker.
Задача 4
Использование нескольких отличных систем виртуализации может повлечь за собой ряд проблем:
1. Они могут создать конфликт системных ресурсов, который приведет к неопределенному поведению, включая сбои виртуальных машин, зависаниям или перезагрузкам, возможно, повреждению данных.
2. Небезопасно загружать драйверы ядра для разных решений визуализации одновременно
3. Судя по найденной информации, только один гипервизор может использовать функции аппаратного ускорения, предлагаемые современными материнскими платами/чипсетами, поэтому один гипервизор может работать в режиме виртуализации программного обеспечения, что может ограничить выбор гостей виртуальной машины.
4. Можно столкнуться с исчерпанием ресурсов, т.к один гипервизор будет не знать, что делает другой.
5. Эксплуатация множества виртуалок повлечет за собой привлечение более компетентого персонала

Если нет возможности не вовлекать гетерогенную среду виртуализации в эксплуатацию, то одним из решений минимизации рисков может стать использование платных, ведущих гипервизоров, которые будут иметь возможность тончайшей настройки распределения ресурсов и разграничение используемых ресурсов сети/портов и тд. Как говорит интернет, минимально конфликтующие между собой являются Hyper-V и Xen. Если бы у меня был выбор, однозначно, использование нескольких систем виртуализации я бы постарался обойти. 

