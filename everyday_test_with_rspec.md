Everyday Rails Testing with RSpec
====

**gems**
• rspec-rails includes RSpec itself in a wrapper to add some extra Rails-specific features.
• factory_girl_rails replaces Rails’ default fixtures for feeding test data to the test suite with much more preferable factories.
• faker generates names, email addresses, and other placeholders for factories.
• capybara makes it easy to programatically simulate your users’ interactions
with your web application.
• database_cleaner helps make sure each spec run in RSpec begins with a clean
slate, by–you guessed it–cleaning data from the test database.
• launchy does one thing, but does it well: It opens your default web browser on demand to show you what your application is rendering. Very useful for
debugging tests.
• selenium-webdriver will let us test JavaScript-based browser interactions with
Capybara.
