# ChatGPT as a tutor


**can you please write the A Star algorithm in python and explain it using haversine**


>code is in notebook
and explanation is The A* algorithm calculates the f(n) value for each node, which is the sum of g(n) and h(n):
f(n)=g(n)+h(n)
The node with the smallest f(n) value is selected to explore next. The algorithm continues until it finds the goal node.
>g(n) is the cost from the start node to n and h(n) is the heuristic estimate of the cost from node n to the goal node

**why is my answer always wrong when using haversine is it because my radians are wrong?
        earthRadius = 6371
        latitude1, longitude1 = coord1
        latitude2, longitude2 = coord2
        radLat1, radLat2 = math.radians(latitude1), math.radians(longitude2)
        deltaLat = math.radians(latitude2 - latitude1)
        deltaLon = math.radians(longitude2 - longitude1)
        #using the haversine math formulas
        a = math.sin(deltaLat / 2) ** 2 + math.cos(radLat1) * math.cos(radLat2) * math.sin(deltaLon / 2) ** 2
        c = 2 * math.atan2(math.sqrt(a), math.sqrt(1 - a))
        #in kilometers
        return earthRadius * c**

>You assigned radLat2 using longitude2 instead of latitude2.
Latitude and Longitude Ranges:
Make sure the coordinates you're passing in (i.e., coord1 and coord2) are indeed in degrees, as the conversion to radians is necessary for the trigonometric functions to work correctly


**why do you need to use radians for haversine and not degrees**

>Most programming languages, including Python, define trigonometric functions such as sin(), cos(), and tan() to take input in radians. For instance, in Python’s math module, functions like math.sin() and math.cos() expect the input angle to be in radians.

Use bold text for prompts and blockquotes or code blocks for ChatGPT's responses.

