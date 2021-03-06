# Требования


Программный продукт *MeMap* предназначен для сохранения заметок с
привязкой ко времени и геолокации.

Программный продукт *MeMap* состоит из следующих подсистем:



## Подсистемы:

### Frontend:
1. Модуль отображения карты (FE_Map)
2. Модуль списка заметок (FE_List)
3. Добавление записи (FE_New)
4. Визуализация профиля (FE_Profile)

### Backend:
1. БД (BE_DB)
2. Авторизация (BE_Auth)
3. Бизнес-логика:
	1. CRUD (BE_Business_CRUD)
	2. Совместимость и корректность записей (BE_Bn_Control)

## Требования

**Требования к подсистеме «Модуль отображения карты»**

Требование FE\_Map\_001

Система должна отображать карту города, в котором находится
пользователь. Если нет возможности определить местоположение
пользователя, то отобразить карту города Владивосток.

Требование FE\_Map\_002

Для каждой записи с заданной геометкой на карте должна быть отображена
метка соответствующая этой заметке. Если к одной точке на карте
привязано больше одной заметки, то на соответствующем маркере должно
быть отображено число привязанных к данной точке карты заметок.

Требование FE\_Map\_003

По запросу пользователя система должна отобразить на карте путь от
точки, соответствующей ближайшей по времени заметке до точки,
соответствующей самой поздней по времени заметке. Если известно
положение пользователя, то к составленному пути прибавляется путь от
положения пользователя до точки, соответствующей ближайшей по времени
заметке.

**Требования к подсистеме «Модуль списка заметок»**

Требование FE\_List\_001

Система должна отображать список актуальных на донный момент заметок для
данного пользователя. Список должен быть отсортирован по времени каждой
заметке от ближайшей по времени до самой поздней.

Требование FE\_List\_002

Заметка, содержащаяся в списке, представляет из себя совокупность
следующих элементов: текста заметки, время/диапазон времени заданное для
донной заметки.

Требование FE\_List\_003

Если у заметки задана геолокация, то при нажатии на данную заметку
соответствующая ей метка на карте должна быть выделена.

**Требования к подсистеме «Добавление записи»**

Требование FE\_New\_001

Система должна предоставлять пользователю интерфейс для добавления новой
заметки. В данном интерфейсе пользователь должен иметь возможность
задать текст заметки, время или диапазон времени для данной заметки и по
желанию указать положение на карте для данной заметки.

Требование FE\_New\_002

При нажатии на незанятую точку карты (для данной точки не задано не
одной заметки) пользователю отображается интерфейс добавления заметки с
привязкой к данной точке. Если точка на карте занята, то будут
отображены все заметки, привязанные к этой точке и кнопка добавления
новой заметки с привязкой к данной точке.

**Требования к подсистеме «Визуализация профиля»**

Требование FE\_Profile\_001

Система должна предоставлять пользователю интерфейс для регистрации и
авторизации в системе.

Требование FE\_Profile\_002

Если пользователь авторизован в системе, то он может посмотреть данные
своего профиля.

**Требования к подсистеме «БД»**

Требование BE\_DB\_001

Система должна содержать базу данных, которая должна хранить информацию
о пользователях и информацию о заметках каждого пользователя.

**Требования к подсистеме «Авторизация»**

Требование BE\_Auth\_001

Система должна предоставлять возможность создания нового пользователя.

Требование BE\_Auth\_002

Система должна предоставлять возможность авторизации пользователя в
системе.

**Требования к подсистеме «CRUD»**

Требование BE\_Bn\_CRUD\_001

Система должна предоставлять возможность добавления, удаления и
изменения информации о заметках в базе данных.

**Требования к подсистеме «Совместимость и корректность записей»**

Требование BE\_Bn\_Control\_001

При добавлении новой заметки система должна проверить данную заметку на
совместимость с текущими заметками. Под несовместимостью понимается
ситуация, при которой время между соседними с данной заметками
значительно меньше минимального времени необходимого для преодоления
расстояния между токами, к которым привязаны данные заметки. При
обнаружении несовместимости система должна выдать пользователю
предупреждение.
