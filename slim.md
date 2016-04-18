Slim Commands
====

**make an html elem equal to text**
h1 = @category.title
or
p = @article.description

**ul's and li's**
ul
- @articles.each do |a|
  li
    a href=(category_articles_path @category, a) = a.title

**comments**
- / for ruby comments
- /! for html comments

**whitespaces**
- can add leading whitespace by adding <
  - i.e. a< href='url1' Link1
- can add trailing whitespace by adding >
  - i.e. a> href='url1' Link1
- can add both with <>
  - i.e. a<> href='url1' Link1
