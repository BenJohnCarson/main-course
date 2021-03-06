# Capybara Setup


## Install Gems
```
$ gem install "capybara"

$ gem install "selenium-webdriver"

$ brew install geckodriver
```

## Firefox
```
Download latest version of Firefox
```

## Test Capybara in IRB or PRY
```ruby
$ require 'capybara'
=> true
$ require 'selenium-webdriver'
=> true
$ require 'capybara/dsl'
=> true
$ include Capybara::DSL
=> including Capybara::DSL in the global scope is not recommended!
$ Capybara.default_driver = :selenium
=> :selenium
$ visit 'http://capybaraworkout.herokuapp.com'
=> Opens website in Firefox
$ click_link 'Start Workout!'
=> Starts workout
```

## Navigating
```ruby
visit('/projects')
visit(post_comments_path(post))
```

## Clicking links and buttons
```ruby
click_link('id-of-link')
click_link('Link Text')
click_button('Save')
click('Link Text') # Click either a link or a button
click('Button Value')
```

## Interacting with forms
```ruby
fill_in('First Name', with: 'John')
fill_in('Password', with: 'Seekrit')
fill_in('Description', with: 'Really Long Text…')
choose('A Radio Button')
check('A Checkbox')
uncheck('A Checkbox')
attach_file('Image', '/path/to/image.jpg')
select('Option', from: 'Select Box')
```

## Scoping
```ruby
within("//li[@id='employee']") do
  fill_in 'Name', with: 'Jimmy'
end
within(:css, "li#employee") do
  fill_in 'Name', with: 'Jimmy'
end
within_fieldset('Employee') do
  fill_in 'Name', with: 'Jimmy'
end
within_table('Employee') do
  fill_in 'Name', with: 'Jimmy'
end
```

## Querying
```ruby
expect(page).to have_xpath?('//table/tr')
expect(page).to have_css?('table tr.foo')
expect(page).to have_content?('foo')
expect(page).to have_xpath('//table/tr')
expect(page).to have_css('table tr.foo')
expect(page).to have_content('foo')
expect(page).to_not have_content('foo')
find_field('First Name').value
find_link('Hello').visible?
find_button('Send').click
find('//table/tr').click
locate("//*[@id='overlay'").find("//h1").click
all('a').each { |a| a[:href] }
```

## Scripting
```ruby
result = expect(page).to evaluate_script('4 + 4');
Asynchronous JavaScript
click_link('foo')
click_link('bar')
expect(page).to have_content('baz')
expect(page).to_not have_xpath('//a')
expect(page).to have_no_xpath('//a')
XPath and CSS
within(:css, 'ul li') { ... }
find(:css, 'ul li').text
locate(:css, 'input#name').value
Capybara.default_selector = :css
within('ul li') { ... }
find('ul li').text
locate('input#name').value
```
