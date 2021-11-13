---
title: Home
---

# Fetch

[Home page](README.md)
[About](about.md)

<div id="output"></div>
<script>
    let testPromise = fetch('https://forexlaravel.herokuapp.com/api/test', {
    method: 'GET',            
    })
    .then(function (response) {
        return response.json()
    })
    .then(function (arr) {
        let element = document.querySelector('#output').appendChild(document.createElement('table'))
        element = element.appendChild(document.createElement('thead'))
        element = element.appendChild(document.createElement('tr'))
        for (let i = 0; i < arr.length; i++) { 
            let response = arr[i]
            console.log(response)
            if(i == 0) {
                for (const key of Object.keys(response)) {
                    let temp = element.appendChild(document.createElement('th'))
                    temp.appendChild(document.createTextNode(`${key}`))
                }
            }
            element = document.querySelector('table').appendChild(document.createElement('tbody'))
            element = element.appendChild(document.createElement('tr'))
            for (const value of Object.values(response)) {
                let temp = element.appendChild(document.createElement('td'))
                temp.appendChild(document.createTextNode(`${value}`))
            }
        }
    })
</script>
