=========
Helm 関連
=========

設定値
======

Exastro Platform
----------------

.. list-table:: Exastro Platform における Values 一覧
   :widths: 25 25 5 5 20
   :header-rows: 1
   :align: left

   * - キー
     - 説明
     - 変更可否
     - 必須
     - 設定値
   * - .global.authGlobalDefinition.name
     - 認証機能の定義名
     - 不可
     - ○
     - auth-global
   * - .global.authGlobalDefinition.enabled
     - 認証機能の利用有無
     - 不可
     - ○
     - true
   * - .global.authGlobalDefinition.image.registry
     - 認証機能で利用するデフォルトイメージレジストリ
     - 不可
     - ○
     - "docker.io"
   * - .global.authGlobalDefinition.image.organization
     - 認証機能で利用するデフォルトイメージレジストリの組織名
     - 不可
     - ○
     - exastro
   * - .global.authGlobalDefinition.image.package
     - 認証機能で利用するデフォルトイメージレジストリのパッケージ名
     - 不可
     - ○
     - exastro-platform
   * - .global.authGlobalDefinition.config.DEFAULT_LANGUAGE
     - 認証機能で使用する既定の言語
     - 不可
     - ○
     - "ja"
   * - .global.authGlobalDefinition.config.LANGUAGE
     - 認証機能で使用する言語
     - 不可
     - ○
     - "en"
   * - .global.authGlobalDefinition.config.TZ
     - 認証機能で使用するタイムゾーン
     - 不可
     - ○
     - "Asia/Tokyo"
   * - .global.authGlobalDefinition.config.PYTHONIOENCODING
     - 認証機能で使用する Python ファイルの文字コード
     - 不可
     - ○
     - utf-8
   * - .global.authGlobalDefinition.config.PLATFORM_API_PROTOCOL
     - 認証機能で公開する内部の API エンドポイントで利用するプロトコル
     - 不可
     - ○
     - "http"
   * - .global.authGlobalDefinition.config.PLATFORM_API_HOST
     - 認証機能で公開する内部の API エンドポイントで利用するホスト名
     - 不可
     - ○
     - "platform-api"
   * - .global.authGlobalDefinition.config.PLATFORM_API_PORT
     - 認証機能で公開する内部の API エンドポイントで利用するポート番号(TCP)
     - 不可
     - ○
     - "8000"
   * - .global.authGlobalDefinition.config.PLATFORM_WEB_PROTOCOL
     - 認証機能で公開する内部の Web エンドポイントで利用するプロトコル
     - 不可
     - ○
     - "http"
   * - .global.authGlobalDefinition.config.PLATFORM_WEB_HOST
     - 認証機能で公開する内部の Web エンドポイントで利用するホスト名
     - 不可
     - ○
     - "platform-web"
   * - .global.authGlobalDefinition.config.PLATFORM_WEB_PORT
     - 認証機能で公開する内部の Web エンドポイントで利用するポート番号(TCP)
     - 不可
     - ○
     - "8000"
   * - .global.authGlobalDefinition.persistence.enabled
     - | 認証機能におけるデータの永続化の有無
       | ※現在このパラメータは使用していません。
     - 可 (無効)
     - ○
     - | :program:`true` (デフォルト): 永続化する。
       | :program:`false`: 永続化しない。
   * - .global.authGlobalDefinition.persistence.accessMode
     - | 認証機能における Persisten Volume Claim のアクセスモード
       | ※現在このパラメータは使用していません。
     - 可 (無効)
     - ○
     - | :program:`ReadWriteMany` (デフォルト): ボリュームは多数のNodeで読み取り専用としてマウント。
       | :program:`ReadWriteOnce`: ボリュームは単一のNodeで読み取り/書き込みとしてマウント。
   * - .global.authGlobalDefinition.persistence.size
     - | 認証機能における Persisten Volume Claim のボリュームに要求するサイズ(Bytes)
       | ※現在このパラメータは使用していません。
     - 可 (無効)
     - ○
     - "10Gi"
   * - .global.authGlobalDefinition.persistence.volumeType
     - | 認証機能における Persisten Volume のボリュームタイプ
       | Storage Class を利用する場合は設定は不要です。
       | ※現在このパラメータは使用していません。
     - 可 (無効)
     - ○
     - "hostPath"
   * - .global.authGlobalDefinition.persistence.storageClass
     - | 認証機能におけるデータの永続化のために利用する Storage Class
       | Persistent Volume を利用する場合は設定は不要です。
       | ※現在このパラメータは使用していません。
     - 可 (無効)
     - ○
     - "-"
   * - .global.keycloakDefinition.name
     - Keycloak の定義名
     - 可
     - ○
     - "keycloak"
   * - .global.keycloakDefinition.enabled
     - Exastro Platform と同一のクラスタ内への Keycloak のデプロイ要否
     - 不可
     - ○
     - | :program:`true` (デフォルト): 同一クラスタ内に Keycloak をデプロイします。
       | :program:`false` : 同一クラスタ内に Keycloak をデプロイしません。(別途 Keycloak の容易が必要です。)
   * - .global.keycloakDefinition.config.API_KEYCLOAK_PROTOCOL
     - Keycloak API エンドポイントのプロトコル
     - 可
     - ○
     - "http”
   * - .global.keycloakDefinition.config.API_KEYCLOAK_HOST
     - Keycloak API エンドポイントのホスト名、もしくは、FQDN
     - 可
     - ○
     - "keycloak.exastro-platform.svc"
   * - .global.keycloakDefinition.config.API_KEYCLOAK_PORT
     - Keycloak API エンドポイントのポート番号
     - 可
     - ○
     - "8080"
   * - .global.keycloakDefinition.config.KEYCLOAK_PROTOCOL
     - Keycloak エンドポイントのプロトコル
     - 可
     - ○
     - "http"
   * - .global.keycloakDefinition.config.KEYCLOAK_HOST
     - Keycloak エンドポイントのホスト名、もしくは、FQDN
     - 不可
     - ○
     - "keycloak.exastro-platform.svc"
   * - .global.keycloakDefinition.config.KEYCLOAK_PORT
     - Keycloak API エンドポイントのポート番号
     - 不可
     - ○
     - "8080"
   * - .global.keycloakDefinition.config.KEYCLOAK_MASTER_REALM
     -
     - 不可
     - ○
     - "master"
   * - .global.keycloakDefinition.config.KEYCLOAK_DB_DATABASE
     -
     - 不可
     - ○
     - "keycloak"
   * - .global.keycloakDefinition.secret.KEYCLOAK_USER
     -
     - 不可
     - ○
     - ""
   * - .global.keycloakDefinition.secret.KEYCLOAK_PASSWORD
     -
     - 不可
     - ○
     - ""
   * - .global.keycloakDefinition.secret.KEYCLOAK_DB_USER
     -
     - 不可
     - ○
     - ""
   * - .global.keycloakDefinition.secret.KEYCLOAK_DB_PASSWORD
     -
     - 不可
     - ○
     - ""
   * - .global.itaDefinition.name
     -
     - 不可
     - ○
     - "ita"
   * - .global.itaDefinition.enabled
     -
     - 不可
     - ○
     - "true"
   * - .global.itaDefinition.config	".global.itaDefinition.config.ITA_WEB_PROTOCOL
     -
     - 不可
     - ○
     - http"
   * - .global.itaDefinition.config.ITA_WEB_HOST
     -
     - 不可
     - ○
     - "ita-web-server.exastro-it-automation.svc"
   * - .global.itaDefinition.config.ITA_WEB_PORT
     -
     - 不可
     - ○
     - "8000"
   * - .global.itaDefinition.config.ITA_API_PROTOCOL
     -
     - 不可
     - ○
     - "http"
   * - .global.itaDefinition.config.ITA_API_HOST
     -
     - 不可
     - ○
     - "ita-api-organization.exastro-it-automation.svc"
   * - .global.itaDefinition.config.ITA_API_PORT
     -
     - 不可
     - ○
     - "8080"
   * - .global.itaDefinition.config.ITA_API_ADMIN_PROTOCOL
     -
     - 不可
     - ○
     - "http"
   * - .global.itaDefinition.config.ITA_API_ADMIN_HOST
     -
     - 不可
     - ○
     - "ita-api-admin.exastro-it-automation.svc"
   * - .global.itaDefinition.config.ITA_API_ADMIN_PORT
     -
     - 不可
     - ○
     - "8080"
   * - .global.authDatabaseDefinition.name
     -
     - 不可
     - ○
     - "auth-database"
   * - .global.authDatabaseDefinition.enabled
     -
     - 不可
     - ○
     - "true"
   * - .global.authDatabaseDefinition.config.DB_VENDOR
     -
     - 不可
     - ○
     - "mariadb"
   * - .global.authDatabaseDefinition.config.DB_HOST
     -
     - 不可
     - ○
     - "mariadb.exastro-platform.svc"
   * - .global.authDatabaseDefinition.config.DB_PORT
     -
     - 不可
     - ○
     - "3306"
   * - .global.authDatabaseDefinition.config.DB_DATABASE
     -
     - 不可
     - ○
     - "platform"
   * - .global.authDatabaseDefinition.secret.DB_ADMIN_USER
     -
     - 不可
     - ○
     - ""
   * - .global.authDatabaseDefinition.secret.DB_ADMIN_PASSWORD
     -
     - 不可
     - ○
     - ""
   * - .global.authDatabaseDefinition.secret.DB_USER
     -
     - 不可
     - ○
     - ""
   * - .global.authDatabaseDefinition.secret.DB_PASSWORD
     -
     - 不可
     - ○
     - ""
   * - .global.databaseDefinition.name
     -
     - 不可
     - ○
     - "mariadb"
   * - .global.databaseDefinition.enabled
     -
     - 不可
     - ○
     - "true"
   * - .global.databaseDefinition.secret.MARIADB_ROOT_PASSWORD
     -
     - 不可
     - ○
     - ""
   * - .global.databaseDefinition.persistence.enabled
     -
     - 不可
     - ○
     - "true"
   * - .global.databaseDefinition.persistence.reinstall
     -
     - 不可
     - ○
     - "false"
   * - .global.databaseDefinition.persistence.accessMode
     -
     - 不可
     - ○
     - "ReadWriteOnce"
   * - .global.databaseDefinition.persistence.size
     -
     - 不可
     - ○
     - "20Gi"
   * - .global.databaseDefinition.persistence.volumeType
     -
     - 不可
     - ○
     - "hostPath"
   * - .global.databaseDefinition.persistence.storageClass
     -
     - 不可
     - ○
     - "-"
   * - .platform-api.image.repository
     -
     - 不可
     - ○
     - "exastro/exastro-platform-api"
   * - .platform-api.image.tag
     -
     - 不可
     - ○
     - "1.0.6"
   * - .platform-auth.ingress.enabled
     -
     - 不可
     - ○
     - "true"
   * - .platform-auth.ingress.hosts[0].host
     -
     - 不可
     - ○
     - "exastro-suite.example.local"
   * - .platform-auth.ingress.hosts[0].paths[0].path
     -
     - 不可
     - ○
     - "/"
   * - .platform-auth.ingress.hosts[0].paths[0].pathType
     -
     - 不可
     - ○
     - "Prefix"
   * - .platform-auth.ingress.hosts[0].paths[0].backend
     -
     - 不可
     - ○
     - "http"
   * - .platform-auth.ingress.hosts[1].host
     -
     - 不可
     - ○
     - "exastro-suite-mng.example.local"
   * - .platform-auth.ingress.hosts[1].paths[0].path
     -
     - 不可
     - ○
     - "/"
   * - .platform-auth.ingress.hosts[1].paths[0].pathType
     -
     - 不可
     - ○
     - "Prefix"
   * - .platform-auth.ingress.hosts[1].paths[0].backend
     -
     - 不可
     - ○
     - "httpMng"
   * - .platform-auth.service.type
     -
     - 不可
     - ○
     - "ClusterIP"
   * - .platform-auth.image.repository
     -
     - 不可
     - ○
     - "exastro/exastro-platform-auth"
   * - .platform-auth.image.tag
     -
     - 不可
     - ○
     - "1.0.6"
   * - .platform-setup.keycloak.image.repository
     -
     - 不可
     - ○
     - "exastro/exastro-platform-job"
   * - .platform-setup.keycloak.image.tag
     -
     - 不可
     - ○
     - "1.0.6"
   * - .platform-web.image.repository
     -
     - 不可
     - ○
     - "exastro/exastro-platform-web"
   * - .platform-web.image.tag
     -
     - 不可
     - ○
     - "1.0.6"
   * - .mariadb.image.repository
     -
     - 不可
     - ○
     - "mariadb"
   * - .mariadb.image.tag
     -
     - 不可
     - ○
     - "10.9"
   * - .mariadb.image.pullPolicy
     -
     - 不可
     - ○
     - "IfNotPresent"
   * - .mariadb.resources.requests.memory
     -
     - 不可
     - ○
     - "256Mi"
   * - .mariadb.resources.requests.cpu
     -
     - 不可
     - ○
     - "1m"
   * - .mariadb.resources.limits.memory
     -
     - 不可
     - ○
     - "2Gi"
   * - .mariadb.resources.limits.cpu
     -
     - 不可
     - ○
     - "4"
   * - .keycloak.image.repository
     -
     - 不可
     - ○
     - "exastro/keycloak"
   * - .keycloak.image.tag
     -
     - 不可
     - ○
     - "1.0.6"
   * - .keycloak.image.pullPolicy
     -
     - 不可
     - ○
     - "IfNotPresent"
   * - .keycloak.resources.requests.memory
     -
     - 不可
     - ○
     - "256Mi"
   * - .keycloak.resources.requests.cpu
     -
     - 不可
     - ○
     - "1m"
   * - .keycloak.resources.limits.memory
     -
     - 不可
     - ○
     - "2Gi"
   * - .keycloak.resources.limits.cpu
     -
     - 不可
     - ○
     - "4"

Exastro IT Automation
---------------------

.. list-table:: Exastro IT Automation における Values 一覧
   :widths: 25 25 5 5 20
   :header-rows: 1
   :align: left

   * - .global.itaGlobalDefinition.name
     - 
     - 不可
     - ○
     - ita-global 
   * - .global.itaGlobalDefinition.enabled
     - 
     - 不可
     - ○
     - true 
   * - .global.itaGlobalDefinition.image.registry
     - 
     - 不可
     - ○
     - docker.io 
   * - .global.itaGlobalDefinition.image.organization
     - 
     - 不可
     - ○
     - exastro 
   * - .global.itaGlobalDefinition.image.package
     - 
     - 不可
     - ○
     - exastro-it-automation 
   * - .global.itaGlobalDefinition.config.DEFAULT_LANGUAGE
     - 
     - 不可
     - ○
     - ja 
   * - .global.itaGlobalDefinition.config.LANGUAGE
     - 
     - 不可
     - ○
     - en 
   * - .global.itaGlobalDefinition.config.CONTAINER_BASE
     - 
     - 不可
     - ○
     - kubernetes 
   * - .global.itaGlobalDefinition.config.TZ
     - 
     - 不可
     - ○
     - Asia/Tokyo 
   * - .global.itaGlobalDefinition.config.STORAGEPATH
     - 
     - 不可
     - ○
     - /storage/ 
   * - .global.itaGlobalDefinition.persistence.enabled
     - 
     - 不可
     - ○
     - true 
   * - .global.itaGlobalDefinition.persistence.accessMode
     - 
     - 不可
     - ○
     - ReadWriteMany 
   * - .global.itaGlobalDefinition.persistence.size
     - 
     - 不可
     - ○
     - 10Gi 
   * - .global.itaGlobalDefinition.persistence.volumeType
     - 
     - 不可
     - ○
     - hostPath 
   * - .global.itaGlobalDefinition.persistence.storageClass
     - 
     - 不可
     - ○
     - - 
   * - .global.gitlabDefinition.name
     - 
     - 不可
     - ○
     - gitlab 
   * - .global.gitlabDefinition.enabled
     - 
     - 不可
     - ○
     - true 
   * - .global.gitlabDefinition.config.GITLAB_PROTOCOL
     - 
     - 不可
     - ○
     - http 
   * - .global.gitlabDefinition.config.GITLAB_HOST
     - 
     - 不可
     - ○
     - gitlab.exastro-platform.svc 
   * - .global.gitlabDefinition.config.GITLAB_PORT
     - 
     - 不可
     - ○
     - 80 
   * - .global.gitlabDefinition.secret.GITLAB_ROOT_TOKEN
     - 
     - 不可
     - ○
     -  
   * - .global.itaDatabaseDefinition.name
     - 
     - 不可
     - ○
     - ita-database 
   * - .global.itaDatabaseDefinition.enabled
     - 
     - 不可
     - ○
     - true 
   * - .global.itaDatabaseDefinition.config.DB_VENDOR
     - 
     - 不可
     - ○
     - mariadb 
   * - .global.itaDatabaseDefinition.config.DB_HOST
     - 
     - 不可
     - ○
     - mariadb.exastro-platform.svc 
   * - .global.itaDatabaseDefinition.config.DB_PORT
     - 
     - 不可
     - ○
     - 3306 
   * - .global.itaDatabaseDefinition.config.DB_DATABASE
     - 
     - 不可
     - ○
     - ITA_DB 
   * - .global.itaDatabaseDefinition.secret.DB_ADMIN_USER
     - 
     - 不可
     - ○
     -  
   * - .global.itaDatabaseDefinition.secret.DB_ADMIN_PASSWORD
     - 
     - 不可
     - ○
     -  
   * - .global.itaDatabaseDefinition.secret.DB_USER
     - 
     - 不可
     - ○
     -  
   * - .global.itaDatabaseDefinition.secret.DB_PASSWORD
     - 
     - 不可
     - ○
     -  
   * - .ita-api-admin.replicaCount
     - 
     - 不可
     - ○
     - 1 
   * - .ita-api-admin.image.repository
     - 
     - 不可
     - ○
     - exastro/exastro-it-automation-api-admin 
   * - .ita-api-admin.image.tag
     - 
     - 不可
     - ○
     - 2.0.1 
   * - .ita-api-admin.image.pullPolicy
     - 
     - 不可
     - ○
     - IfNotPresent 
   * - .ita-api-organization.replicaCount
     - 
     - 不可
     - ○
     - 1 
   * - .ita-api-organization.image.repository
     - 
     - 不可
     - ○
     - exastro/exastro-it-automation-api-organization 
   * - .ita-api-organization.image.tag
     - 
     - 不可
     - ○
     - 2.0.1 
   * - .ita-api-organization.image.pullPolicy
     - 
     - 不可
     - ○
     - IfNotPresent 
   * - .ita-by-ansible-execute.replicaCount
     - 
     - 不可
     - ○
     - 1 
   * - .ita-by-ansible-execute.image.repository
     - 
     - 不可
     - ○
     - exastro/exastro-it-automation-by-ansible-execute 
   * - .ita-by-ansible-execute.image.tag
     - 
     - 不可
     - ○
     - 2.0.1 
   * - .ita-by-ansible-execute.image.pullPolicy
     - 
     - 不可
     - ○
     - IfNotPresent 
   * - .ita-by-ansible-execute.extraEnv.EXECUTE_INTERVAL
     - 
     - 不可
     - ○
     - 10 
   * - .ita-by-ansible-execute.extraEnv.ANSIBLE_AGENT_IMAGE
     - 
     - 不可
     - ○
     - exastro/exastro-it-automation-by-ansible-agent 
   * - .ita-by-ansible-execute.extraEnv.ANSIBLE_AGENT_IMAGE_TAG
     - 
     - 不可
     - ○
     - 2.0.0 
   * - .ita-by-ansible-execute.serviceAccount.create
     - 
     - 不可
     - ○
     - false 
   * - .ita-by-ansible-execute.serviceAccount.name
     - 
     - 不可
     - ○
     - ita-by-ansible-execute-sa 
   * - .ita-by-ansible-legacy-role-vars-listup.replicaCount
     - 
     - 不可
     - ○
     - 1 
   * - .ita-by-ansible-legacy-role-vars-listup.extraEnv.EXECUTE_INTERVAL
     - 
     - 不可
     - ○
     - 10 
   * - .ita-by-ansible-legacy-role-vars-listup.image.repository
     - 
     - 不可
     - ○
     - exastro/exastro-it-automation-by-ansible-legacy-role-vars-listup 
   * - .ita-by-ansible-legacy-role-vars-listup.image.tag
     - 
     - 不可
     - ○
     - 2.0.1 
   * - .ita-by-ansible-legacy-role-vars-listup.image.pullPolicy
     - 
     - 不可
     - ○
     - IfNotPresent 
   * - .ita-by-ansible-towermaster-sync.replicaCount
     - 
     - 不可
     - ○
     - 1 
   * - .ita-by-ansible-towermaster-sync.extraEnv.EXECUTE_INTERVAL
     - 
     - 不可
     - ○
     - 10 
   * - .ita-by-ansible-towermaster-sync.image.repository
     - 
     - 不可
     - ○
     - exastro/exastro-it-automation-by-ansible-towermaster-sync 
   * - .ita-by-ansible-towermaster-sync.image.tag
     - 
     - 不可
     - ○
     - 2.0.1 
   * - .ita-by-ansible-towermaster-sync.image.pullPolicy
     - 
     - 不可
     - ○
     - IfNotPresent 
   * - .ita-by-conductor-synchronize.replicaCount
     - 
     - 不可
     - ○
     - 1 
   * - .ita-by-conductor-synchronize.extraEnv.EXECUTE_INTERVAL
     - 
     - 不可
     - ○
     - 10 
   * - .ita-by-conductor-synchronize.image.repository
     - 
     - 不可
     - ○
     - exastro/exastro-it-automation-by-conductor-synchronize 
   * - .ita-by-conductor-synchronize.image.tag
     - 
     - 不可
     - ○
     - 2.0.1 
   * - .ita-by-conductor-synchronize.image.pullPolicy
     - 
     - 不可
     - ○
     - IfNotPresent 
   * - .ita-by-menu-create.replicaCount
     - 
     - 不可
     - ○
     - 1 
   * - .ita-by-menu-create.extraEnv.EXECUTE_INTERVAL
     - 
     - 不可
     - ○
     - 10 
   * - .ita-by-menu-create.image.repository
     - 
     - 不可
     - ○
     - exastro/exastro-it-automation-by-menu-create 
   * - .ita-by-menu-create.image.tag
     - 
     - 不可
     - ○
     - 2.0.1 
   * - .ita-by-menu-create.image.pullPolicy
     - 
     - 不可
     - ○
     - IfNotPresent 
   * - .ita-database-setup-job.image.repository
     - 
     - 不可
     - ○
     -  
   * - .ita-database-setup-job.image.tag
     - 
     - 不可
     - ○
     -  
   * - .ita-database-setup-job.image.pullPolicy
     - 
     - 不可
     - ○
     - IfNotPresent 
   * - .ita-web-server.replicaCount
     - 
     - 不可
     - ○
     - 1 
   * - .ita-web-server.image.repository
     - 
     - 不可
     - ○
     - exastro/exastro-it-automation-web-server 
   * - .ita-web-server.image.tag
     - 
     - 不可
     - ○
     - 2.0.1 
   * - .ita-web-server.image.pullPolicy
     - 
     - 不可
     - ○
     - IfNotPresent 
