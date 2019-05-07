## ActiveRecord methods

Let us suppose we have a table called "contacts" with columns `first_name`, `last_name`, `date_of_birth`, `created_at`, `updated_at`, and `id`.

Our model file would look like this:
```
# == Schema Information
#
# Table name: contacts
#
#  id            :integer          not null, primary key
#  date_of_birth :date
#  first_name    :string
#  last_name     :string
#  created_at    :datetime         not null
#  updated_at    :datetime         not null

class Contact < ApplicationRecord
end
```
Note that the class `Contact` inherits from `ApplicationRecord`.

### CRUD

#### Create

Creating a new instance of the `Contact` class and adding values through its `attr_accessors`.
```
c = Contact.new
c.first_name = "Raghu"
c.last_name = "Betina"
```

Saving a new instance to the contacts table.  
`c.save`

#### Read 

**.all:**  
Returns all the rows of a table.
`contact_list = Contact.all`  
`.all` returns an object like an Array, known as a "collection."


**.count:**
Returns the number of entries in the table.  
`Contact.all.count # => 1`  
or  
`Contact.count # => 1`

**.first:**  
Returns the first entry(row) in the table.
`first_contact = Contact.all.first`  
or  
`first_contact = Contact.first`

**.last:**  
Returns the last entry(row) in the table.
`last_contact = Contact.all.last`  
or  
`last_contact = Contact.last`

Since the `.all` is optional, we can omit it.
**.order:**  
Orders the rows in the table based on one or more attributes of the table. `.order` takes a *Hash* as an argument.  
`Contact.order({ :last_name => :asc })`  
To break ties we can use multiple column attributes in the `Hash`  
`Contact.order({ :last_name => :asc, :first_name => :asc, :date_of_birth => :desc })`  

**.reverse:**  
Reverses the ordering of a collection.
`Contact.order(:first_name).reverse`  
This above line will return the same thing as:  
`Contact.order({ :last_name => :desc })`  

**.where:**  
`.where` takes a `Hash` as an argument where the *key* is column you filter by and the *value* is the criteria you filter by.  
`Contact.where({ :id => 2 }) # will return return a collection with one contact whose id is 2`


***Note:***  
`.where` returns a collection and not a single row.

To break ties or look for a very specific entry in the table we can filter by more than one column or chaining together `.where` methods.   
`Contact.where({ :last_name => "Mouse", :first_name => "Minnie" }) # will return a collection of contacts with last_name = "Mouse" and first_name = "Minnie"`  
or  
`Contact.where({ :last_name => "Mouse" }).where({ :first_name => "Minnie" }) # will return a collection of contacts with last_name = "Mouse" and first_name = "Minnie"`  

You can use an Array to broaden your search criteria.
`Contact.where({ :last_name => ["Betina", "Woods"] }) # will return a collection of contacts with last_name = "Betina" or last_name = "Woods"`

**.or:**  
You can also broaden your search criteria by using the `.or` method.
`Contact.where({ :first_name => "Mickey" }).or(Contact.where({ :last_name => "Betina" })) # will return a collection of contacts whose first_name = "Mickey" or last_name = "Betina"`  

**.not:**   
You can negate a criteria with `.not`  
`Contact.where.not({ :first_name => "Mickey" }) # will return a collection of contacts whose first_name is not "Mickey"`

**.pluck:**  
`.pluck` method returns an Array of values from a single column in the given collection.  
`Contact.where({ :last_name => "Mouse" }).pluck(:first_name) # => ["Minnie", "Mickey"]`
 
#### Update 
Updating a row is very similar to creating a row but first you have to locate the row you want to update. 
```
c = Contact.first
c.first_name = "Miverva"
```
Now that you have updated the row, you have to save it  
`c.save`

#### Delete
Like updating, to delete a row first you have to locate the row you want to delete and then use the `.destroy` method to remove the row from the table. 
```
c = Contact.first
c.destroy
```
