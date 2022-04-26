---
layout: post
title:04-05 In Class Notes [4/05/22]
---

# In Class Notes
-Need to add authentication line now (think phishing - you do not want to delete other accounts, etc)
> "cross-site request forgery"
- <input type="hidden" name="authenticity_token" value="<%= form_authenticity_token %>">

- now should use a[1] instead of a.at(1) for accessing arrays
- it's the same for ActiveRecord_Relation (.at will not work there)
- prefer .fetch() for hashes instead of [] because it will throw an error sooner - the [] will return a nil and the error will come later in the code


- **.find_by** will find the record and take the first value out ie. @the_movie = Movie.find_by({ :id => the_id })
- potential returns for .find_by are a record or nil (same as where().first)
> **.find** will only take a single value to search in the ID column, find_by will take in a hash
- .find will return a record or raise ActiveRecord::RecordNotFound; in production mode sends a 404 page


-Raise keyword gives the ability to do an exception on purpose, create an error; don't want the code to proceed further and will log in error system to help later debug
