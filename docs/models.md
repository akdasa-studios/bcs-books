# Models

```mermaid
classDiagram

class Language {
    +string code
    +string name
}

class MediaUrl {
    +string url
    +Resolution resolution
}

class Chapter {
    +ChapterId id
    +BookId bookId
    +string title
    +language language
    +order number
}

class Book {
    +BookId id
    +string title
    +language language
}

class Page {
    +PageId id
    +ChapterId chapterId
    +order number
    +string content
}

class Media {
    +MediaId id
    +PageId pageId
    +Resolution resolution
    +string description
}

Chapter o-- Language : written in
Book o-- Language : written in
Book <-- Chapter : belongs to
Page --> Chapter : belongs to
Media --> Page : belongs to
Media --> MediaUrl : at
```

# Value Objects

`Language` - is a value object to determine the language of a `Book` or `Chapter`. `Language` has a `code` fied which is a two letter code of the language. For example `en` for English, `de` for German, `fr` for French, etc.
