# String Urlize [![Build Status](https://secure.travis-ci.org/cheef/string-urlize.png "Build Status")](http://travis-ci.org/cheef/string-urlize) [![Dependency Status](https://gemnasium.com/cheef/string-urlize.png "Dependency Status")](https://gemnasium.com/cheef/string-urlize)

Extends ruby ```String``` class with ```urlize``` method which converts string to friendly url.
It removes all characters that couldn't be used in url and replaces spaces/underscores with dashes.
In addition it transliterate string using I18n library.

## Installation

    gem install string-urlize

In Rails 3, add this to your Gemfile and run the bundle command.

    gem "string-urlize"

## Usage

    'my cool string'.urlize # => my-cool-string
    :foo_symbol.to_s.urlize # => foo-symbol

Examples:

<table>
  <tr><th>string</th><th>url</th></tr>
  <tr><td>Lorem ipsum dolor sit amet</td><td>lorem-ipsum-dolor-sit-amet</td></tr>
  <tr><td>CamelCase</td><td>camel-case</td></tr>
  <tr><td>a   lot   of   spaces</td><td>a-lot-of-spaces</td></tr>
  <tr><td>special !@#$%^&*()<>,./?\ \|  symbols</td><td>special-symbols</td></tr>
  <tr><td>underscored_string</td><td>underscored-string</td></tr>
  <tr><td>string with-dashes</td><td>string-with-dashes</td></tr>
  <tr><td>ÈÉÊË</td><td>eeee</td></tr>
  <tr><td>òóôõöø</td><td>oooooo</td></tr>
</table>

## Transliteration

Transliteration powered by I18n library and enabled by default. So you could provide locale to the urlize method:

    'Jürgen'.urlize                 # => "jurgen"
    'Jürgen'.urlize(:locale => :de) # => "juergen"

or disable transliteration at all:

    'Jürgen'.urlize(:transliterate => false) # => 'jürgen' in ruby 1.9 and 'jrden' in ruby 1.8.7

