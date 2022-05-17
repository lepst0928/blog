---
layout: post
title: In-Class Notes [5/17/22]
---

# Week 8 Notes - In-Class Notes


creating the json api
https://api.rubyonrails.org/classes/ActiveModel/Serializers/JSON.html
```ruby
class UsersController < ApplicationController
  def show
    @user = User.find(params[:id])

    render(json: @user.as_json(
      # only: [:id, :username]
      include: [:feed]
    ))
  end
end
```

making an API request (in javascript/react)
```javascript
export default function Feed(){
	const [feed, setFeed] = useState(data);
	useEffect(() => {
		getFeed();
	},[])
function getFeed()
	const url = "https://google.com/whatever.json"
	const options = {
		method: "GET",
		headers: {
		Accept: "application/json",
		"Content-type": "application/json"
		}
		}
	
	fetch(url)
		.then((response) => response.json())
		.then((data) => console.log(data))
	);
const posts = feed.map((post) => (
```

**jbuilder** readme: https://github.com/rails/jbuilder


