# MonthType Enumeration Project

This project involves creating a custom `MonthType` enumeration that represents the months of the year, along with their properties such as month codes, the number of days, and the corresponding seasons. The program includes a test class to demonstrate the functionality of the `MonthType` enum.

## Objective

Create a Java program that:

- Implements the `MonthType` enum with the following features:
    - `String name()`: Returns the name of the month (e.g., JANUARY).
    - `int value()`: Returns the month code (1 for January, 2 for February, etc.).
    - `int daysOfMonth()`: Returns the number of days in the month (without considering leap years).
    - `MonthType getMonth(int monthCode)`: Returns a `MonthType` object for a given integer value.
    - `SeasonType getSeason()`: Returns the season (as an enum type `SeasonType`) that the month belongs to.

## Enumeration: SeasonType

The `SeasonType` enum represents the four seasons:
- WINTER
- SPRING
- SUMMER
- AUTUMN

## Example Implementation

### MonthType.java

```java
public enum MonthType {
    JANUARY(1, 31, SeasonType.WINTER),
    FEBRUARY(2, 28, SeasonType.WINTER),
    MARCH(3, 31, SeasonType.SPRING),
    APRIL(4, 30, SeasonType.SPRING),
    MAY(5, 31, SeasonType.SPRING),
    JUNE(6, 30, SeasonType.SUMMER),
    JULY(7, 31, SeasonType.SUMMER),
    AUGUST(8, 31, SeasonType.SUMMER),
    SEPTEMBER(9, 30, SeasonType.AUTUMN),
    OCTOBER(10, 31, SeasonType.AUTUMN),
    NOVEMBER(11, 30, SeasonType.AUTUMN),
    DECEMBER(12, 31, SeasonType.WINTER);

    private final int monthCode;
    private final int days;
    private final SeasonType season;

    MonthType(int monthCode, int days, SeasonType season) {
        this.monthCode = monthCode;
        this.days = days;
        this.season = season;
    }

    public int value() {
        return monthCode;
    }

    public int daysOfMonth() {
        return days;
    }

    public static MonthType getMonth(int monthCode) {
        for (MonthType month : MonthType.values()) {
            if (month.value() == monthCode) {
                return month;
            }
        }
        throw new IllegalArgumentException("Invalid month code: " + monthCode);
    }

    public SeasonType getSeason() {
        return season;
    }
}
```

### SeasonType.java

```java
public enum SeasonType {
    WINTER,
    SPRING,
    SUMMER,
    AUTUMN
}
```

### TestProgram.java

```java
public class TestProgram {
    public static void main(String[] args) {
        // Loop to output all months with their month code and number of days
        for (MonthType month : MonthType.values()) {
            System.out.printf("%s - Month %d - Number of days: %d%n", 
                month.name(), month.value(), month.daysOfMonth());
        }

        // Conversion from MonthType object into Integer
        MonthType month1 = MonthType.JANUARY;
        System.out.printf("Conversion: Month %s -> Integer %d%n", 
            month1.name(), month1.value());

        // Conversion from Integer to MonthType object
        MonthType month2 = MonthType.getMonth(1);
        System.out.printf("Conversion: Integer %d -> Month %s%n", 
            1, month2.name());

        // Check if the converted MonthType objects are the same
        System.out.printf("Month %s and month2 %s are equal.%n", 
            month1.name(), month2.name());

        // Loop to detect and output all summer months
        System.out.println("The summer months:");
        for (MonthType month : MonthType.values()) {
            if (month.getSeason() == SeasonType.SUMMER) {
                System.out.print(month.name() + " ");
            }
        }
    }
}
```

## Example Output

When you run the `TestProgram` class, the output should look like this:

```
JANUARY - Month 1 - Number of days: 31
FEBRUARY - Month 2 - Number of days: 28
MARCH - Month 3 - Number of days: 31
APRIL - Month 4 - Number of days: 30
MAY - Month 5 - Number of days: 31
JUNE - Month 6 - Number of days: 30
JULY - Month 7 - Number of days: 31
AUGUST - Month 8 - Number of days: 31
SEPTEMBER - Month 9 - Number of days: 30
OCTOBER - Month 10 - Number of days: 31
NOVEMBER - Month 11 - Number of days: 30
DECEMBER - Month 12 - Number of days: 31
Conversion: Month JANUARY -> Integer 1
Conversion: Integer 1 -> Month JANUARY
Month JANUARY and month2 JANUARY are equal.
The summer months:
JUNE JULY AUGUST 
```

## Notes

- Ensure that you have the necessary Java environment set up to compile and run the program.
- This implementation does not account for leap years; February is fixed at 28 days. You may want to enhance the `MonthType` enum to handle leap years if needed.
- You can extend the functionality of the `MonthType` enum by adding more methods or properties as required.

Happy coding! 🎉