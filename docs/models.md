# Models

```
classDiagram

class Language {
    +string code
    +string name
}

class Chapter {
    +BookId bookId
    +string title
    +language language
    +order number
}

class Book {
    +string title
    +language language
}

class Page {
    +ChapterId chapterId
    +order number
    +string content
}

Chapter o-- Language : written in
Book o-- Language : written in
Book <-- Chapter : belongs to
Page <-- Chapter : belongs to
```

# Value Objects

`Language` - is a value object to determine the language of a `Book` or `Chapter`. `Language` has a `code` fied which is a two letter code of the language. For example `en` for English, `de` for German, `fr` for French, etc.
