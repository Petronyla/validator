# Validator - Advanced Java Assignment
Your task is to implement a class called `Validator` which will have two public static methods:

*  `boolean isValid(Object o)` – determines if the argument `o` is valid according to the rules described below
*  `void validate(Object o)` – if the argument `o` is not valid, then throws `ValidationException`, otherwise does nothing

## Validation
Classes are validated according to the annotations present on the fields. Example:

```java
class C {
	@MyAnnotation
	Object field1;
}
```

Each annotation has a special meaning which represents specific constraint. These annotations will need to be created by you. Annotations to create:

* `@AssertFalse` – the field must be a `boolean` with a value of `false`
* `@AssertTrue` – the field must be a `boolean` with a value of `true`
* `@Future` – the field must be a `LocalDateTime` and the value must specify time in future
* `@Ignored` – the field will not be validated. This annotation supersedes the importance of other annotations
* `@NotBlank` – the field must be a `String` with non-whitespace character
* `@NotNull` – the field value cannot be `null`
* `@Null` – the fiel value must be `null`
* `@Pattern` – the field must be a `String` which adheres to the regex specified in `regex` attribute
  
  Attributes:
  * `regex` – (`String`) regex to which the value must adhere
* `@Size` –  specifies the size of the value. Can be applied to multiple types which changes semantics a little.
  Allowed types:
  * `String` – length is evaluated
  * `Collection`  – collection size is evaluated
  * `Map` – map size is evaluated
  * `Array` – array length is evaluated
  
  Attributes:
  
  * `min` – (`int`) specifies the minimum allowed value (included)
  * `max` – (`int`) specifies the maximum allowed value (included)

**Note**: Every annotation will have one additional attribute `message` (`String`, `""` by default) which will be used in the `validate` method which will pass the value to `ValidationException`. 

## Tests
Once the implementation is complete, please write a bunch of unit tests to prove that your solution is working. You don't need to use testing framework (e.g. JUnit), you can just use one test class with main method which will call the "tests".