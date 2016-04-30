Rails Conference BDD
====

- I'm at time 1:00:42

**Before Block**
- This makes it so that before each test is run you initialize a new cart:

describe "An instance of", Cart do
  before :each do
    @cart = Cart.new
  end
end:

- In this case we are using a hash to hold our items and delegating to the @items#empty? method:

class Cart
  def initialize
    @items = {}
  end

  def empty?
    @items.empty?
  end
end

**Red-Green-Refactor (RGR)**
- In the REFACTOR state, we concentrate on making the current implementation better, cleaner and more robust
- It is very likely that early on in the development there won't be much to refactor
- The need for refactoring is a side-effect of increasing complexity and interaction between classes and subsystems
- Refactoring can also introduce implementation specific specs or reveal holes in your previous specs

**Ruby's Forwardable module**
- Ruby's Forwardable module simplifies the delegation of collection methods to the @items Hash
class Cart
  extend Forwardable
  def_delegator :@items, :empty?

  def initialize
    @items = {}
  end
end

RSpec & Capybara
====
**Acceptance Testing**
- Proper acceptance tests treat your application as a black box
- They should know as little as possible about what happens under the hood
- They're just there to interact with the interface and observe the results
- "A great testing strategy is to extensively cover the data layer with unit tsts and then skip all the way up to acceptance tests.  This apporach gives great code coverage and builds a test suite that can flex with a changing codebase."

**Capybara: Acceptance test framework for web applications**
- Capybara is a lightweight alternative to Cucumber
- Capybara is a browser automation library
- Helps you test web apps by simulating how a real user would interact with your app
- It is agnostic about the driver running your tests and comes with Rack::Test and Selenium support built in
- (it seems like Rack::Test is an alternative to Selenium)
- WebKit is supported through an external gem

**RSpec, Capybara, and Steak**
- Many developers don't want to bother with Cucumber
- They want outside-in testing without the translation step
- The Steak project integrated RSpec and Capybara directly
- Now we can write acceptance tests just like you write unit tests, greatly simplifying the process
- In late 2010, Capybara absorbed the Steak syntax

**Rack::Test**
- Capybara uses Rack::Test by default
- Rack::Test interacts with your app at the Rack level
- It runs requests against the app, then provides the resulting HTML to Capybara and RSpec for examination
- Rack::Test is completely headless (and therefore fast)
- The disadvantage is that it doesn't process JavaScript (or give you visual feedback)
- To test JavaScript in your acceptance tests, you can use the selenium-webdriver or capybara-webkit driver

**Check thoughtbot Capybara Domain Specific Language Cheatsheat, for things like Navigation, Page Assertions, Node Interactions, Form Interactions, CSS, etc**

**Acceptance Testing with Capybara**
- We are going to mimic a user's interaction with a very simple Rails app
- The bulk of the functionality in the app will be provided by the devise (authentication) library and the high_voltage (static pages) gems
- To concentrate on the subtleties of Capybara we will test an existing application at https://github.com/integrallis/learn-rspec-capybara





