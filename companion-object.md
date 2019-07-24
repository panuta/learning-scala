# Companion Object

```scala
class Email(val username: String, val domainName: String)

object Email {
  def fromString(emailString: String): Option[Email] = {
    emailString.split('@') match {
      case Array(a, b) => Some(new Email(a, b))
      case _ => None
    }
  }
}

val scalaCenterEmail = Email.fromString("scala.center@epfl.ch")
scalaCenterEmail match {
  case Some(email) => println(
    s"""Registered an email
       |Username: ${email.username}
       |Domain name: ${email.domainName}
     """)
  case None => println("Error: could not parse email")
}
```

ใช้มากในกรณีที่ต้องการสร้าง Factory pattern โดยการใส่ factory function ใน companion object \(จากตัวอย่างด้านบนคือ fromString\) ซึ่งจะ return instance ของ class นั้น

