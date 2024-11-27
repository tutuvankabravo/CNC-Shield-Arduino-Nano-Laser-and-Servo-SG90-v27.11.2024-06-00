# CNC-Shield-Arduino-Nano-Laser-and-Servo-SG90-v27.11.2024 06-00 - актуальная  
CNC-Shield-Arduino-Nano-Laser-and-Servo-SG90-v26.11.2024 - не использовать  

Версия прошивки v27.11.2024 06-00 (LASER and SERVO SG90)  

Описание работы:  
Файл конфигурации должен считываться с SD Card накопителя.  
Не все люди умеют программировать, написать текст в блокноте намного проще и его можно перевести на разные языки.  
Пример строки:  
$0 = 10 //(Step pulse time, microseconds метод тыка)//  
$1 = 25 //(Step idle delay, milliseconds от 0 до 255)//  
$2 = 0 //(Step pulse invert, maskот 0 до 7, $6 = 0 нет инверсии, $6 = 1 инверсия X, $6 = 2 инверсия Y, $6 = 3 инверсия XY)//  
$3 = 0 //(Step direction invert, mask 0 до 7, $6 = 0 нет инверсии, $6 = 1 инверсия X, $6 = 2 инверсия Y, $6 = 3 инверсия XY)//  
$4 = 0 //(Invert step enable pin, boolean 0 - концевик сработает если замкнуть на GND, 1 - концевик сработает если замкнуть на +5V)//  
$5 = 0 //(Invert limit pins, boolean 0 - отключить концевик, 1 - включить концевик)//  
$11 = 0.010 //(Junction deviation, millimeters - отклонения на стыках в миллиметрах)//  
$12 = 0.002 //(Arc tolerance, millimeters - отклонение от дуги)//  
$13 = 0 //(Report in inches, boolean 0 - вывод на экран текущих позиций в мм, 1 - вывод на экран текущих позиций в дюймах.)//  
$20 = 0 //(Soft limits enable, boolean 0 - перед отправко G-кода не проверяет границы предела, 1 - проверяет границы предела осей)//  
$21 = 0 //(Hard limits enable, boolean 0 - концевики выключены, 1 - концевики включены)//  
$22 = 0 //(Homing cycle enable, boolean 0 - поиск домашней позиции отключена, 1 - домашняя позиция включена)//  
$23 = 0 //(Homing direction invert, mask 0 - нет инверсии осей, 1 - инверсия X, 2 - инверсия Y, 3- инверсия XY)//  
$24 = 25.000 //(Homing locate feed rate, mm/min - Скорость подачи при поиске начальной точки Дома)//  
$25 = 500.000 //(Homing search seek rate, mm/min - Скорость самонаведения? мм/мин)//  
$26 = 250 //(Homing switch debounce delay, milliseconds - подавление дребезга контактов концевиков при поиске начальной точки ДОМ, миллисекнды)//  
$27 = 1.000 //(Homing switch pull-off distance, millimeters - отъезд от начальной точки мм)//  
$32 = 0 // (Laser-mode enable, boolean 0 - меняет мощность лазера притормаживая ХУ, 1 - меняет мощность лазера не притормаживая)//  
или $33 = 0 // от 0 до 2 ( 0 - Лазер логический, подаёт на ножку D9 логическое питание ардуино +5 Вольт)//  
или $33 = 1 // от 0 до 2 ( 1 - Лазер ШИМ, подаёт на ножку D9 ШИМ сигнал) //  
или $33 = 2 // от 0 до 2 ( 2 - Серво привод SG90, подаёт на ножку D9 сигнал серво привода)//  
$100 = 250.000 // (X-ось разрешение шага двигателя, step/mm) //  
$101 = 250.000 // (Y-ось разрешение шага двигателя, step/mm)//  
$110 = 500.000 // (X-axis maximum rate, mm/min - максимальная скорость перемещения оси X)//  
$111 = 500.000 // (Y-axis maximum rate, mm/min - максимальная скорость перемещения оси Y))//  
$120 = 10.000  // (X-axis acceleration, mm/sec^2 - ускорения при начале движения осей)//  
$121 = 10.000  // (Y-axis acceleration, mm/sec^2 - ускорения при начале движения осей))//  
$130 = 200.000 // (X-axis maximum travel, millimeters - максимально перемещение (рабочая область))//  
$131 = 200.000 // (Y-axis maximum travel, millimeters - максимально перемещение (рабочая область))//  
$6  -  убрать эту команду (не использовать)  
$10 -  убрать эту команду (не использовать)  
$30 -  убрать эту команду (не использовать)  
$31  - убрать эту команду (не использовать)  
$102 - убрать эту команду (не использовать)  
$112 - убрать эту команду (не использовать)  
$122 - убрать эту команду (не использовать)  
$132 - убрать эту команду (не использовать)
  
Формат конфигурационного файла conf.txt :     
При включении Arduino nano создаёт файл на SD CARD, с текущими настройками станка "conf.txt" которые можно посмотреть через блокнот и если надо изменить.   
Если файл "conf.txt" уже существует на флешке, то новый файл создан не будет.  
Таким образом файл конфигурации будет всегда на SD Card накопителе и не потеряется.  
Если SD CARD не вставлена то на дисплее должна быть надпись "нет SDCARD".  
Если SD CARD карта вставлена и на карте есть данные то отобразить их на дисплее LCD1602.  
Пример файлов на SD CARD:  
conf.txt  
drill_12.nc  
circle2.nc  
12345678.nc  
Название файлов не должно превышать 8 символов ?  
  
Управление кнопками START, STOP, UP, DOWN:  

  
Подключенные пины Ардуино Нано:  
Чтение с SD Card (с U1 на U9), пины на ардуино нано D12-MISO, D11-MOSI, D13-SCK, D10-CS  
Управление Лазером (с U1 на XP14) D9-PWM L (состояние меняется в конфигурации conf.txt $33 = 1)  
Управление Servo SG90 (с U1 на XP13) D9-PWM S (состояние меняется в конфигурации conf.txt $33 = 2)  
Управление Лазер логический или катушкой реле +5V (логика) (с U1 на ХР13 и XP14) D9-+5V (состояние меняется в конфигурации conf.txt $33 = 0)  

Кнопки меню:  
Кнопка START (ПУСК-OK) (с XP18 на U9) A6  
Кнопка STOP (остановить) (с XP19 на U9) A7  
Кнопка UP (вверх) (с XP2 на U9) A1  
Кнопка DOWN (вниз) (с XP2 на U9) A0  

Подключение LCD1602 по шине I2C:  
пин (Ардуины U9) A4 = SDA, пин (Ардуины U9) A5 = SCL

Работа станка:  
