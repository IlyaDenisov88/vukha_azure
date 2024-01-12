# Аналитическая лабораторная Azure. 7 вариант.
## Команда Вуха:
* Калачева Вера К3223
* Петрова Виктория К3223
* Денисов Илья К3223
* Марков Даниил К3223

## Цель работы: 
Знакомство с облачными сервисами. Понимание уровней абстракции над инфраструктурой в облаке. Формирование понимания типов потребления сервисов в сервисной-модели. Сопоставление сервисов между разными провайдерами. Оценка возможностей миграции на отечественные сервисы.

## Дано:
1. Слепок данных биллинга от провайдера после небольшой обработки в виде SQL-параметров. Символ % в начале/конце означает, что перед/после него может стоять любой набор символов.
2. Google с документациями провайдера.

## Таблица


## Описание сервисов Azure
1. **Azure SQL Database** - это сервис для создания, хранения, использования и масштабирования реляционных баз данных в облаке. Предоставляет функциональность для различных сценариев синхронизации данных.

  Рассмотрим некоторые подсервисы и виды услуг, предоставляемых Azure SQL Database.
  
  * Пользователю предлагаются различные уровни обслуживания(General Purporse, Business Critical, Hyperscale), в зависимости от необходимых мощностей.
  *  Кроме того, имеются два варианта использования ресурсов: **Single Database** и **Elastic Pool**. Single Database создает базу данных в Azure с собственным набором ресурсов и управляется с помощью сервера. При Single Database данных каждая БД изолирована и использует выделенные только ей ресурсы. Elastic Pool - решение для управления и масштабирования нескольких баз данных с переменными и непредсказуемыми требованиями к использованию. Базы данных в пуле находятся на одном сервере и совместно используют определенное количество ресурсов по установленной цене.
  *  Также существуют две "модели закупок": **vCore** и **DTU**. vCore обеспечивает более детальный контроль над ресурсами и позволяет самостоятельно масштабировать вычислительные ресурсы и ресурсы хранения в зависимости от ваших конкретных потребностей. Эта модель подходит для предприятий с особыми требованиями к производительности и желающих получить больший контроль над распределением ресурсов. DTU обеспечивает комплексное измерение ресурсов вычислений, памяти и ввода-вывода, что облегчает пользователям понимание производительности. Эта модель подходит для предприятий, которые предъявляют менее сложные требования к производительности и предпочитают упрощенную модель ценообразования и ресурсов.
  *   Сервис предоставляет возможности резервного копирования. Базово резервные копии хранятся 7 дней, с возможностью продления до 35 дней(point-in-time-restore). Опция **Long-term retention(LTR)** обеспечивает автоматическое сохранение резервных копий в отдельных контейнерах Azure Blob на срок до 10 лет.
  * Опция **Reserved Capacity** помогает экономить вычислительные ресурсы. Вместо стандартного ценообразования pay-as-you-go предлагается вариант резервирования вычислительных ресурсов сроком на 1 или 3 года. Таким образом можно получить значительную скидку на стоимость вычислений.

2. **Azure SQL Managed Instance** - это полностью управляемая PaaS, которая обрабатывает большинство функций управления базами данных, таких как обновление, исправление, резервное копирование и мониторинг без участия пользователя. Azure SQL Managed Instance предоставляет полностью управляемый экземпляр SQL Server, позволяя использовать все возможности и функциональность SQL Server. Это особенно полезно для организаций, которым необходимо перенести рабочие нагрузки локального SQL Server в облако. 
Сервис предоставляет аналогичные возможности резервного копирования, выбора уровня обслуживания, что и SQL Database.

3. **Azure Synapse Analytics** - это корпоративный аналитический сервис, который ускоряет время получения информации в хранилищах данных и системах больших данных. Azure Synapse Analytics предлагает возможности интеграции данных, которые позволяют организациям получать, подготавливать и преобразовывать данные из различных источников в содержательные сведения. Сервис представляет собой полностью управляемое хранилище данных (**Data Warehouse**), способное обрабатывать петабайты данных. Он позволяет организациям хранить, управлять и анализировать большие объемы данных для целей бизнес-аналитики и отчетности.

4. **Azure  Backup** - это экономичное, безопасное решение для резервного копирования, которое можно масштабировать в зависимости от потребностей в хранении резервных копий. Централизованный интерфейс управления позволяет легко определять политики резервного копирования и защищать широкий спектр корпоративных рабочих нагрузок, включая виртуальные машины Azure, базы данных SQL и SAP, а также общие файловые ресурсы Azure. 

Сервис имеет в себе два различных подсервиса хранилищ резервных копий: Recovery Service vault и Backup vault.

**Recovery Service vault** это традиционная служба, используемая Azure Backup в качестве хранилища для данных резервного копирования. До недавнего времени, если вы использовали Azure Backup для своих виртуальных машин, будь то в Azure или в помещении, вы использовали Recovery Services Vault. Recovery Service vault имеет большую совместимость с другими сервисами Azure для резервного копирования, например Azure Site Recovery data. Вы можете использовать различные политики резервного копирования для различных рабочих нагрузок, включая расширенные варианты политик, которые поддерживают самые последние функции Azure, такие как: ВМ с доверенным запуском, поддержка Ultra SSD, поддержка общих дисков, многократное ежедневное резервное копирование и т. д.

**Backup vault** представляет собой централизованное и легкодоступное место для хранения и управления резервными копиями данных и приложений. Это хранилище не используется для выполнения полного последовательного резервного копирования приложений виртуальных машин, а предлагает возможность резервного копирования на управляемые диски Azure. Оно обеспечивает устойчивое к сбоям резервное копирование данных для дисков с ОС и данными путем создания инкрементных снимков диска в регулярное время, вплоть до каждого часа. Ключевое отличие от Recovery Service vault заключается в том, что данные не переносятся в хранилище для долгосрочного хранения, а вместо этого вам предоставляется оперативное средство резервного копирования. С вас взимается только стоимость дельта-изменений в хранилище моментальных снимков, поэтому плата за услуги резервного копирования не взимается. 

5. **Azure Storage** - это облачное решение Microsoft для современных сценариев хранения данных. Azure Storage предлагает высокодоступное, масштабируемое, долговечное и безопасное хранилище для различных объектов данных в облаке. 

Azure Storage включает в себя множество подсервисов: 
  Azure Blobs: Масштабируемое объектное хранилище для текстовых и бинарных данных. Также включает поддержку аналитики больших данных с помощью Data Lake Storage Gen2.
  Azure Files: Управляемые файловые ресурсы для облачных и локальных развертываний.
  Azure Elastic SAN: Полностью интегрированное решение, упрощающее развертывание, масштабирование, управление и настройку SAN в Azure.
  Azure Queues: Хранилище сообщений для надежного обмена сообщениями между компонентами приложения.
  Azure Tables: NoSQL-хранилище для бессхемного хранения структурированных данных.
  Azure managed Disks: Тома хранения на уровне блоков для виртуальных машин Azure.
  Azure Container Storage: Служба управления томами, развертывания и оркестровки, созданная специально для контейнеров.

  Сервис Azure Blob Storage поддерживает большие объемы неструктурированных данных, что делает его подходящим для хранения наборов данных и обучающих моделей для приложений машинного обучения, в том числе Microsoft Machine Learning Services.

  Batch - это сервис для эффективного выполнения крупномасштабных параллельных и высокопроизводительных вычислений (HPC) с помощью пакетных заданий в Azure. Batch создает и управляет пулом вычислительных узлов (виртуальных машин), устанавливает приложения, которые вы хотите запустить, и планирует выполнение заданий на узлах. Хранилище **Azure Queue** предоставляет решение для обмена сообщениями для надежной связи между компонентами приложения. Оно может использоваться в Microsoft Batch для управления сообщениями, связанными с заданиями, и координации между различными задачами пакетной обработки.
  6. **Azure Virtual Machines** - это сервис, который позволяет создавать Linux и Windows виртуальные машины (VMs) за секунды. Сервис предоставляет широкие возможности масштабирования, резервного копирования и совместим с другими сервисами Azure, что позволяет, например отслеживать производительность в режиме реального времени и автоматизировать управление виртуальными машинами с помощью Azure Monitor и Application Insights. Обеспечивает гибкость виртуализации без необходимости покупать и обслуживать физическое оборудование, на котором работает виртуальная машина.
  7. **Azure BizTalk Services** - это облачный интеграционный сервис, предоставляющий возможности Business-to-Business (B2B) и Enterprise Application Integration (EAI) для облачных и гибридных интеграционных решений.
  8. **Azure DevOps** - это комплексная платформа для разработки программного обеспечения, которая предлагает ряд возможностей, предназначенных для организации и ускорения разработки на протяжении всего жизненного цикла приложений.
  9. **Azure Monitor** - это комплексное решение для мониторинга, позволяющее собирать, анализировать и реагировать на данные мониторинга из облачных и локальных сред. Используется для обеспечения максимальной доступности и производительности приложений и служб.
  10. **Azure Web Sites** - это платформа веб-хостинга, поддерживающая множество технологий и языков программирования (. NET, node. js, PHP, Python). Позволяет создавать веб-сайты и размещать на них содержимое и код, обеспечивает быстрое развертывание, легкую настройку, мониторинг, высокую масштабируемость и соглашение об уровне обслуживания (SLA).
  11. **Azure Data and AI** - набор сервисов и решений которые позволяют организациям использовать данные, аналитику и возможности искусственного интеллекта для получения информации, принятия обоснованных решений и создания интеллектуальных приложений. 
 
## Подбор аналагов
| Azure  | Russian |
| ------------- | ------------- |
| Azure SQL Database | Relational Database Service for SQL (cloud.ru) |
| Azure SQL Managed Instance | Yandex Managed Service for YDB  |
| Azure Synapse Analytics | Data Warehouse Service (cloud.ru)  |
| Azure  Backup | Yandex Cloud Backup  |
| Azure Storage  | Yandex Object Storage |
| Azure Virtual Machines | Yandex Compute Cloud |
| Azure BizTalk Services | Entaxy |
| Azure DevOps | DataFort DevopsPlatform |
| Azure Monitor | Yandex Monitoring |
| Azure Web Sites | Yandex Static website hosting |
| Azure Data and AI |  |

## Описание российских сервисов

  1. **Relational Database Service for SQL (cloud.ru)** — это надежный и высокодоступный сервис управления реляционными базами данных. RDS обеспечивает сохранность ваших данных, а механизмы резервного копирования позволяют устранять неисправности за считаные секунды. RDS поддерживает MySQL, PostgreSQL и SQL Server. Автоматическое резервное копирование работает по умолчанию. При необходимости, пользователь может создать резервные копии в ручную, которые будут храниться до момента удаления пользователем. 

  2. **Yandex Managed Service for YDB** помогает разворачивать и поддерживать базы данных YDB в инфраструктуре Yandex Cloud.
  YDB — это распределенная отказоустойчивая Distributed SQL СУБД. YDB обеспечивает высокую доступность, горизонтальную масштабируемость, а также строгую консистентность и поддержку ACID-транзакций. Для запросов используется диалект SQL (YQL). 
  
  Для каждой БД при создании выбирается один из двух режимов работы: Serverless или Dedicated. 
  
  Serverless — БД, не требующая от вас какого-либо конфигурирования, администрирования, отслеживания загрузки и управления ресурсами. Для ее создания достаточно указать имя, и вы получите URL для соединения. Оплата берется за исполнение запросов и фактический объем хранимых данных.
  
  Dedicated — вы определяете вычислительные ресурсы, которые будут зарезервированы под БД: CPU и RAM на узлах, количество узлов и объем хранилища данных. Вам необходимо отслеживать достаточность ресурсов для успешной обработки нагрузки и добавлять новые по мере необходимости. Оплата берется за выделенные ресурсы по часам, вне зависимости от их фактического использования.

  3. **Data Warehouse Service (cloud.ru)** — это безопасное и простое хранилище корпоративных данных, которое обеспечивает анализ больших данных петабайтного объема в разных отраслях промышленности. Сервис совместим со стандартами ANSI SQL 99, SQL 2003 и экосистемами PostgreSQL и Oracle. DWS реализует архитектуру без совместного использования ресурсов и механизм массовой параллельной обработки.
  
  Сервис состоит из многочисленных независимых логических узлов, которые не используют общие системные ресурсы, такие как процессоры, память и хранилище. Данные хранятся отдельно на многочисленных узлах, а задачи обработки и анализа выполняются в месте, ближайшем к данным. Такая массовая параллельная обработка данных обеспечивает быстрый ответ.

  4. **Yandex Cloud Backup**  — это сервис для создания резервных копий и восстановления ресурсов Yandex Cloud и данных на них. Доступно копирование и восстановление виртуальных машин Compute Cloud с поддерживаемыми операционными системами.
  
  Копии ВМ создаются по принципу application-consistent: сохраняются не только данные на дисках, но и данные, которые были отправлены в запись на диск и еще не успели записаться. Такой подход позволяет возобновить работу приложений, запущенных на ВМ в момент создания копии, сразу после восстановления ВМ. Это важно для ВМ, которые входят в состав систем хранения данных. Например, когда на ВМ запущена система управления базами данных (СУБД).
  
  Cloud Backup умеет создавать полные и инкрементальные копии. В полной копии хранятся все данные ВМ — восстановление происходит быстрее, чем из инкрементальной, но такая копия занимает больше места и создается дольше. В инкрементальной копии содержатся только отличия от предыдущей копии, она создается быстрее и занимает меньше места, но восстановление ВМ из такой копии дольше, чем из полной. Если вы понимаете, что с момента создания последней копии в ВМ накопилось много изменений, лучше сделать полную копию ВМ.
  
  Также с помощью Cloud Backup можно восстановить из резервной копии отдельные файлы и директории на любую из ВМ, подключенных к сервису. 

  5. **Yandex Object Storage** — это универсальное масштабируемое решение для хранения данных. Сервис подходит как для высоконагруженных систем, которым требуется надежный и быстрый доступ к данным, так и для проектов с невысокими требованиями к инфраструктуре хранения.
  
  В терминах Object Storage файлы и папки — это объекты. Все объекты размещаются в бакетах. Структура хранения объектов в бакете плоская, но инструменты с графическим интерфейсом предлагают работать с Object Storage как с иерархической файловой системой.
  
  6. **Yandex Compute Cloud** предоставляет масштабируемые вычислительные мощности для создания виртуальных машин и управления ими. Сервис поддерживает прерываемые виртуальные машины, а также отказоустойчивые группы виртуальных машин.

  Сервис дает возможность подключать к виртуальным машинам диски с образами на базе OC Linux, каждый диск автоматически реплицируется внутри своей зоны доступности, что обеспечивает надежное хранение данных. Можно использовать только те вычислительные мощности, которые необходимы для решения конкретной задачи, быстро масштабировать вычислительные мощности, разворачивать на ВМ приложения, которые должны быть постоянно доступны, настроить резервное копирование и Автоматизировать управление ВМ с помощью API и скриптов в интерфейсе командной строки.

  7. **Entaxy** — это «Low-code» платформа, позволяющая создавать и запускать сложные интеграционные маршруты с помощью простых понятных объектов в понятном интерфейсе.
  8. **DataFort DevopsPlatform** — это сервис, позволяющий производить быстрое развёртывание приложений на Java, PHP, Python, Go, Node.js и Ruby без изменения кода, автоматическое развертывание балансировщиков, SQL- и NoSQL баз данных, настройку автоматического горизонтального и вертикального масштабирования. Обеспечивает поддержку Docker-контейнеров и Kubernetes.
  9. **Yandex Monitoring** позволяет собирать и хранить метрики, а также отображать их в виде графиков на дашбордах.

  Сервисные дашборды создаются автоматически после создания ресурсов в Yandex Cloud. Сервисные дашборды представляют собой аналитическую панель, содержащую список облачных продуктов, с которыми у мониторинга уже есть интеграция. Сервис Yandex Compute Cloud не измеряет потребление vRAM внутри гостевой операционной системы: для сервиса потребление памяти ВМ всегда одинаковое — то, которое выделено в момент ее запуска. Также есть возможность самостоятельно настроить сбор пользовательских метрик с помощью запись пользовательских метрик через API, а для Linux-совместимых ОС — с помощью агента для поставки системных метрик. Агент позволяет собирать статистику использования большинства системных ресурсов: процессор, память, сеть, диск.

  10. **Yandex Static website hosting** — это сервис, позволяющий разместить свой статический сайт в Object Storage. Статический сайт строится на клиентских технологиях, таких как HTML, CSS и JavaScript. 

  Object Storage позволяет настроить бакет:
  * Для хостинга статического сайта - необходимо загрузить в бакет содержимое сайта и указать главную страницу сайта
  * Для переадресации всех запросов - можно указать хост, на который будут перенаправляться все запросы, а какже задать протокол для передачи запросов
  * Для условной переадресации запросов - используя правила маршрутизации можно перенаправлять запросы в соответствии с префиксами имен объектов или HTTP-кодами ответов. Вы можете перенаправить на другую веб-страницу запрос к удаленному объекту или перенаправить запросы, возвращающие ошибку.
  Бакет — это контейнер для хранения объектов в хранилище. Для работы хостинга необходим публичный доступ к бакету.

## Вывод

В ходе выполнения лабораторной работы были проанализированы некоторые Azure сервисы, найдены их полные или частичные аналоги в России. Информация о сервисах была взята из официальных документаций Microsoft и российских сервисов. Была заполнена таблица, в которой получилось распределить сервисы Azure ни типы и подтипы, подобрать типы использования. Так как для большинства сервисов были найдены аналоги, можно сделать вывод, что миграция возможна, несмотря на то, что для некоторых сервисов функционал аналогов значительно уже, чем сервисов Azure. Например, сервис Yandex Object Storage, являясь универсальным хранилищем, не полностью предоставляет функционал Azure Storage, который включает в себя множество сервисов, начиная с табличных хранилищ (Azure Table) и заканчивая службой управления томами для контейнеров (Azure Container Storage). Тем не менее, большинство возможностей Azure представлены у отечественных провайдеров.
