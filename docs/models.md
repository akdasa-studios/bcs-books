# Models

```mermaid
classDiagram

class Language {
    <<value>>
    +code: string
    +name: string
}

class Chapter {
    <<entity>>
    +bookId: BookId
    +languageId: LanguageId
    +title: string
    +order: number
}

class Book {
    <<entity>>
    +title: string
    +languageId: LanguageId
}

class Page {
    <<aggregate>>
    +chapterId: ChapterId
    +media: List[Media]
    +order: number
    +content: string
}

class TableOfContext {
    <<aggregate>>
    +bookId: BookId
    +chapters: List[Chapter]
}

class MediaUrl {
    <<value>>
    +url: string
    +quality: MediaQuality
}

class Media {
    <<aggregate>>
    +pageId: PageId
    +description: string
    +urs: List[MediaUrl]
}

class MediaQuality {
    <<enumeration>>
    Low,
    High
}

Chapter --> Language : written in
Chapter "M" --> TableOfContext : belongs to
Book --> Language : written in
Book <-- "M" Chapter : belongs to
Page "M" --> Chapter : belongs to
Media "M" --> Page : belongs to
Media --> "M" MediaUrl : at
MediaUrl --> MediaQuality : of
```

# Value Objects

`Language` - is a value object to determine the language of a `Book` or `Chapter`. `Language` has a `code` fied which is a two letter code of the language. For example `en` for English, `de` for German, `fr` for French, etc.
