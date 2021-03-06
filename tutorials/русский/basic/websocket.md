### Протокол WebSocket

#### 1. Формат протокола WebSocket

WebSocket - это протокол для полнодуплексной связи по одному TCP-соединению. Чтобы установить соединение WebSocket, клиент должен сначала инициировать HTTP-запрос к серверу. Этот запрос отличается от обычного HTTP-запроса и содержит некоторую дополнительную информацию заголовка. Дополнительная информация заголовка «Upgrade: WebSocket» указывает, что это HTTP-запрос на обновление протокола. Request, сервер анализирует эту дополнительную информацию заголовка, а затем генерирует ответное сообщение для возврата клиенту. Соединение WebSocket между клиентом и сервером установлено, и две стороны могут свободно передавать информацию через этот канал соединения, и соединение будет существовать до тех пор, пока Один из клиентов или серверов активно закрывает соединение.

Процесс взаимодействия протокола протокола WebSocket выглядит следующим образом:

![](/assets/websockets_diagram.png)

#### 2. Просмотр протокола WebSocket

HttpCanary поддерживает анализ протокола WebSocket и отображает взаимодействие данных между клиентом и сервером в форме диалога.

![](/assets/websockets_overview.png)







