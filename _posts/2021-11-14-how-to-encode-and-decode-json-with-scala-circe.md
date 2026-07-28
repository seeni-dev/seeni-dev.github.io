---
layout: post
title: "How to Encode and Decode JSON with Scala-Circe"
---

If you are new to the Scala-Circe library and you want to know how to decode/encode JSON, follow the method below.

## Your Classes

Assume your application has a nested class named Person which has a member named **address** of class **Address**.

```scala
case class Address(doorNo: Int, street: String, city: String, zipCode: String)
case class Person(name: String, age: Int, address: Address)
```

## Your Task

You need to encode objects and decode text using Circe and use them following some business logic.

## What to do?

I will give you a simple straightforward approach that will work for 95% of your use cases.

1. Add implicit codec in companion objects for your case classes.
2. Add encode and decode method in the companion object.

```scala
import io.circe._, io.circe.generic.semiauto._, io.circe.syntax._

case class Address(doorNo: Int, street: String, city: String, zipCode: String)
object Address {
  implicit val codec = deriveCodec[Address]
}

case class Person(name: String, age: Int, address: Address)

object Person {
  implicit val codec = deriveCodec[Person]
  def encode(person: Person): String = {
    person.asJson.toString
  }

  def decode(jsonString: String): Person = {
    parser.decode[Person](jsonString).toOption.get
  }
}
```

That’s it. You can now use the `Person.encode` and `Person.decode` methods.

The sample app is below.

```scala
import io.circe._, io.circe.generic.semiauto._, io.circe.syntax._

val johnDoe = Person("John Doe", 24, Address(5, "Times Square Street", "New York", "12345"))
println(Person.encode(johnDoe))


val encodedText = """
{
  "name" : "Fin",
  "age" : 21,
  "address" : {
    "doorNo" : 7,
    "street" : "Staten Island",
    "city" : "New York",
    "zipCode" : "23456"
  }
}
"""
val decodedJohnDoe = Person.decode(encodedText)

println(decodedJohnDoe)
```

If you want to access the runnable version of this code, along with imports and library version, use [scastie link.](https://scastie.scala-lang.org/sy4s1aISQTqX60uUCSlErA)

*First published [here](https://seeni0424.medium.com/getting-started-with-scala-circe-bd2b6ff5d00d)*

*Originally published on [HackerNoon](https://hackernoon.com/how-to-encode-and-decode-json-with-scala-circe).*
