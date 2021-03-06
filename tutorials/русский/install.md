### Установка

#### 1. Настроить VPN (обязательно)

HttpCanary использует VPN для перехвата трафика устройства для реализации захвата пакетов сетевых данных, поэтому VPN необходимо настроить для использования HttpCanary.

![](/assets/install_vpn.png)

<br>

#### 2. Установите корневой сертификат (обязательно)

**Для установки сертификата необходимо, чтобы на устройстве был установлен пароль или шаблон блокировки экрана. Следуйте подсказкам системы, чтобы установить его (это системное ограничение не имеет ничего общего с HttpCanary)**

HttpCanary использует технологию Man-in-the-Middle (MITM) для захвата и анализа пакетов протокола TLS / SSL, таких как распространенные HTTPS, WSS и другие зашифрованные запросы, поэтому перед использованием необходимо установить корневой сертификат HttpCanary. Во время установки нажмите OK по умолчанию, пожалуйста, не изменяйте конфигурацию.

![](/assets/install_user_cetificate.png)

<br>

#### 3. Обновите сертификат до системного (настоятельно рекомендуется 7.0+)

**Этот шаг требует корневого устройства. Настоятельно рекомендуется настроить его для систем выше 7.0 (включительно), а для систем 5.0-6.0 этот шаг можно пропустить.**

Начиная с Android Nougat (7.0), Google изменил свою стратегию сетевой безопасности. Сертификат CA, установленный пользователем, по умолчанию не будет доверенным для соединения TLS / SSL, что означает, что HttpCanary может не иметь возможности захватывать зашифрованные пакеты данных TLS / SSL, а при захвате пакетов нет сети. Мы можем обновить сертификат, установленный на предыдущем шаге, до системного.

##### 3.1 Способ 1. Обновление в один клик в HttpCanary

![](/assets/install_system_cetificate.png)

Этот метод может дать сбой. Если он не удастся, воспользуйтесь другими методами ниже.

##### 3.2 Метод 2: импорт вручную

Сначала экспортируйте файл корневого сертификата, который был установлен на шаге 2 выше. Этот файл можно найти в каталоге / data / misc / user / 0 / cacerts-added / (если файлов несколько, нужно различать по времени), или вы можете экспортировать его на карту памяти SD в настройках корневого сертификата HttpCanary.

![](/assets/cetificate_export.png)

Затем импортируйте файл формата .0 (не переименовывайте его) в системный каталог сертификатов CA / system / etc / security / cacerts /.

Есть много способов импорта:

-adb команда import

Этот метод требует, чтобы был установлен инструмент adb, что подходит для разработчиков Android. Если инструмент adb не установлен, обратитесь к другим методам.

оболочка

# 87bc3517.0 - это файл сертификата, имя подлежит экспорту

корень adb
оболочка adb
монтировать -o rw, remount / system
cp -f /sdcard/HttpCanary/87bc3517.0 / system / etc / security / cacerts
`` ''

-mt manager 2 импорт

Используйте mt manager 2 для импорта файла сертификата и напрямую скопируйте файл сертификата в формате .0 в каталог / system / etc / security / cacerts (вам необходимо смонтировать состояние чтения и записи системы).

![](/assets/cetificate_move.png)

##### 3.3 Успешная проверка обновления сертификата

После успешного обновления системного сертификата вы можете найти добавленный системный сертификат HttpCanary на странице системы «Настройки -> Шифрование и учетные данные -> Надежные учетные данные -> Система».

![](/assets/cetificate_trust.png)

##### 3.4 Примечания

-Эту операцию необходимо выполнить на корневом устройстве.
-Устройства ниже 7.0 не нуждаются в настройке этой опции.
-Обновление / перезапуск системы может привести к удалению файла сертификата сброса системы, проверьте и снова импортируйте.
-После обновления сертификата системы не удаляйте сертификат пользователя, установленный на шаге 2.

<br>

#### 4. Установите сертификат и добавьте его в браузер Firefox.

Firefox очень подходит для захвата пакетов веб-данных, но Firefox использует несистемный сертификат CA для аутентификации, поэтому установленный сертификат HttpCanary не может вступить в силу, и его необходимо добавить в браузер Firefox.

![](/assets/cetificate_firefox1.png)

В интерфейсе установки сертификата Firefox в HttpCanary нажмите «Установить» и выберите Firefox, чтобы открыть его. Firefox автоматически откроет диалоговое окно установки сертификата, отметьте все элементы доверия и подтвердите (** проверьте все параметры **) .

![](/assets/cetificate_firefox2.png)
<br>

#### 5. Установите Parallel Space (настоятельно рекомендуется 7.0+ без полномочий root)

Если версия системы устройства является пользователем без полномочий root выше Android 7.0 (включая), настоятельно рекомендуется установить Parallel Space для помощи в захвате пакетов. Система 5.0-6.0 может игнорировать этот шаг.

**Примечание: Parallel Space не поддерживает версию Android Q**

Корневое устройство требуется для обновления системного сертификата, поэтому для пользователей, которые не могут получить root права на устройство, использование параллельного пространства в качестве средства захвата пакетов может решить проблему отсутствия сети в некоторых приложениях.

##### 5.1 Метод установки

После инициализации HttpCanary найдите вход для установки параллельного пространства в настройках HttpCanary. Если это 64-битное устройство, будут отображены два варианта установки в параллельном пространстве, пожалуйста, устанавливайте их один за другим (один обязательно). Мобильные телефоны с версией 8.0 и выше будут ограничивать источник установки во время установки, пожалуйста, отметьте согласие (вы можете отключить разрешение после завершения установки).

![](/assets/install_paralle_space.png)

**Примечание: версия с параллельным пространством должна использовать встроенную версию HttpCanary, более поздняя, ​​чем эта версия, недопустима для захвата пакетов**

##### 5.2 Использование параллельного пространства

Для некоторых приложений, у которых нет Интернета для захвата пакетов, вы можете использовать Parallel Space, чтобы открыть это приложение (откройте целевое приложение вместо открытия HttpCanary).

![](/assets/paralle_space_capture.png)

Затем используйте HttpCanary для захвата пакетов в параллельном пространстве, а затем вы можете захватывать пакеты данных целевого приложения.

---

#### в заключение

-Мобильные телефоны ниже 7.0, нет необходимости обновлять сертификат, не нужно устанавливать параллельное пространство, захват пакетов очень удобен.
-Мобильные телефоны с версией 7.0 и выше, корневой сертификат обновления, параллельное пространство для установки без рута.


**Это конец руководства по установке! Давайте с радостью начнем использовать HttpCanary!**
