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

You can search for partial matches by passing a fragment of SQL in a String instead of the usual *Hash*  
```
Contact.where("last_name LIKE ?", "%bet%") 
# returns a collection of entries that contain the substring "bet" in their last_name
```
***Note:***  
The above variation of `.where` does an aggressive match and will match even uppercase/lowercase counterparts of the characters in substring.

You can search for rows less than or greater than certain criteria  
`Contact.where("date_of_birth > ?", 30.years.ago)`

You can use the less than or greater than operations to specify a range for the values in a column.  
```
Contact.where("last_name >= ? AND last_name <= ?", "A", "C")`  
      # or  
Contact.where({ :last_name => ("A".."C") })
# will return a collection of contacts whose last_names range from "A" to ""
```
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

#### Other Methods 
**.limit:**  
`.limit` will limit the number of records returned in a collection.  
```
Contact.where({ :last_name => "Mouse" }).limit(10) 
# will return a collection with no more than 10 entries
```

**.offset:**  
`.offset` will return a some rows from a collection by skipping a certain number of rows in between. 
```
the_mouses = Contact.where({ :last_name => "Mouse" })

the_mouses.offset(10) # will return a collection with every 10th entry from the_mouses
```
**.maximum:**  
Returns the entry largest/latest with the attribute in the argument.  
```
Contact.where({ :last_name => "Mouse" }).maximum(:date_of_birth) 
# returns the youngest contact with last_name = "Mouse"
```

**.minimum:**  
Returns the entry smallest/oldest with the attribute in the argument.  
```
Contact.where({ :last_name => "Mouse" }).maximum(:date_of_birth) 
# returns the oldest contact with last_name = "Mouse"
```

**.average:**  
Returns the average value in a particular column whose name is the argument.  
`Review.where({ :venue_id => 4 }).average(:rating)`
