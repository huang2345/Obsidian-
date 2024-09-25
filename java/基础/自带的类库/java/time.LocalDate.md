#### static LocalDate now()
构造一个表示当前日期的对象
#### static LocalDate of(int year,int month,int day)
构造一个表示给定日期的对象
#### int getYear()
#### int getMonthValue()
#### int getDayOfMonth()
获取年月日
#### DayOfWeek getDayOfWeek()
返回一个对象，调用该DayOfWeek对象的getValue()来获取一个1~7之间表示星期几的数。

#### LocalDate plusDays(int n)
#### LocalDate minusDays(int n)
生成当前日期之后或者之前n天的日期