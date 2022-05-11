---
layout: post
title: In-Class Notes [5/10/22]
---

# Week 7 Notes - In-Class Notes

**{ use state } hook**

```javascript
import React, { useState } from "react";
import Tabs from "./Tabs";

export default function Feed() {
    const [tab, setTab] = useState("Posts");
    
    return (
        <>
        <div> Feed </div>
        <Tabs />
        {tab === "Posts"? <div> Posts </div> : <div> Liked Posts </div>}
        </>
    )
}
```


**.map explained**

in React:     
```javascript
const postElements = posts.map ((post) => {
        return (
            <Post />
        );
    })
```
    

in Ruby: 
```ruby
postElements.each do |post|
#turn the post hash into a Post decodeURIComponent
end
```
    

