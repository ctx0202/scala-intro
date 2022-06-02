# ADT


```scala
//Source: https://blog.rockthejvm.com/algebraic-data-types/
object ADTs {
    sealed trait Weather //Sum type
    case object Sunny extends Weather
    case object Windy extends Weather
    case object Rainy extends Weather

    type Weather = Sunny + Windy + Rainy

    def feeling(w: Weather): String = w match {
        case Sunny => "Oh, it's such a beautiful sunny day :D"
        case Windy => "It's cloudy, but at least it's not raining :|"
        case Rainy => "I am very sad. It's raining outside :("
    }

    //Product types
    case class ForecastRequest(val latitude: Double, val longitude: Double)

    //Hybrid types
    sealed trait ForecastResponse
    case class Ok(weather: Weather) extends ForecastResponse
    case class Ko(error: String, description: String) extends ForecastResponse
}
```

## Advantage of ADT:

1. illegal states are NOT representable
   - safer case match
2. highly composable (eg. ForecastResponse can be composed of Weather)
3. just data not functionality => immutable data structures/cleaner code structure