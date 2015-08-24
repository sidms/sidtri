---
layout: post
title: Short Reference for Validations in Active Record
date: 2015-06-21 13:35:30.000000000 +05:30
---


Rails comes with some predefined mixins so that we can use them without writing custom validations everytime

* validates_presence_of
* validates_inclusion_of


###### List of Validations and Clearing them 

<pre>
<code class='language-ruby'>
Modelname.validators # list of array with all our validations
# => [
#      MyValidator:0x007fbff403e808 @options={}>,
#      OtherValidator:0x007fbff403d930 @options={on: :create}>,
#      StrictValidator:0x007fbff3204a30 @options={strict:true}>
#    ]
</code>
</pre>


* Modelname.clear_validators!

###### ActiveModel::Validations (Module)

This will provides <code> validates_each(attributes, options) lambda </code> 

Options

  * on :symbol or array of symbols (eg:: on :create, on [:new, :create]
  * :allow_nil => true, allow_blank
  * :if, :unless string or proc or method
  
<pre>
<code class='language-ruby'>
validates_each :first_name, :last_name do |record, attr, value|
    record.errors.add attr, 'error message' if true
  end
</code>
</pre>



###### Default Validators

Eg:: validates :name , options

options 

* acceptance: true
* confirmation: true
* exclusion: { in: %w(admin superuser) }
* format: { with: /\A([^@\s]+)@((?:[-a-z0-9]+\.)+[a-z]{2,})\z/i, on: :create }
* inclusion: { in: 0..9 }
* length: { maximum: 30 }
* numericality: true
* presence: true
* uniqueness: true
