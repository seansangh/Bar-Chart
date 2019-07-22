# Bar-Chart

*Simple svg graphic*

This is an app that allows you to create a simple bar chart.


...

**Home Page**

<img src="/BarChart.PNG" title="home page" alt="home page" width="500px">


---


## Table of Contents 

> Sections
- [Sample Code](#Sample_Code)
- [Installation](#installation)
- [Features](#features)
- [Contributing](#contributing)
- [Team](#team)
- [FAQ](#faq)
- [Support](#support)
- [License](#license)


---

## Sample Code

```javascript
// svg code

    var w = 750;
    var h = 400;
    
    var dateArr=[];
    var gdpArr=[];
    
    for(var i=0;i<json['data'].length;i++){
      dateArr.push(json['data'][i][0]);
      gdpArr.push(json['data'][i][1]);
    }

    const dateArrMin = d3.min(dateArr, (d) => Date.parse(d)); 
    const dateArrMax = new Date("2015-09-01"); 
    
    const gdpArrMin = d3.min(json["data"], d => d[1]); 
    const gdpArrMax = d3.max(json["data"], d => d[1]); 

    const xScale = d3.scaleTime()
                     .domain([dateArrMin, dateArrMax])
                     .range([0, w]);
    
    const yScale = d3.scaleLinear()
                     .domain([0, gdpArrMax])
                     .range([h, 0]);

    var tooltip = d3.select("body")
                    .append("div")
                    .attr("class", "tooltip")
                    .attr("id", "tooltip")
                    .style("opacity", 0);    
    
    const svg = d3.select("body")
                  .append("svg")
                  .attr("width", w)
                  .attr("height", h);

               svg.selectAll("rect")
                  .data(json["data"])
                  .enter()
                  .append("rect")
                  .attr("x", (d, i) => xScale(Date.parse(d[0])))
                  .attr("y", (d, i) => yScale(d[1]))
                  .attr("width", w / json["data"].length)
                  .attr('height', (d, i) => h - yScale(d[1]))
                  .attr("class", "bar")
                  .attr("fill", "red")
                  .attr("data-gdp", d => d[1])
                  .attr("data-date", d => d[0])
                  .on("mouseover", function(d) {
                      tooltip.transition()
                             .duration(200)
                             .style("opacity", 0.7);
                      tooltip.html("<b>Date:</b> " + d[0] + '<br/>' + "<b>GDP:</b> $" + d[1])
                             .style("left", d3.event.pageX + 10 + "px")
                             .style("top", d3.event.pageY + 10 + "px");
                      tooltip.attr("data-date", d[0]);
                   })
                  .on("mouseout", function(d) {
                      tooltip.transition()
                             .style("opacity", 0);
                   });

    const xAxis = d3.axisBottom(xScale);
    const yAxis = d3.axisLeft(yScale);

    
   svg.append("g")
      .attr("transform", "translate(0," + h + ")")
      .attr("id", "x-axis")
      .call(xAxis);
    
   svg.append("g")
      .attr("transform", "translate(0,0)")
      .attr("id", "y-axis")
      .call(yAxis);
```

---

## Installation
## Features
## Usage (Optional)
## Documentation (Optional)
## Tests (Optional)
## Contributing
## Team

> Contributors/People

| [**seansangh**](https://github.com/seansangh) |
| :---: |
| [![seansangh](https://avatars0.githubusercontent.com/u/45724640?v=3&s=200)](https://github.com/seansangh)    |
| [`github.com/seansangh`](https://github.com/seansangh) | 

-  GitHub user profile

---

## FAQ

- **Have any *specific* questions?**
    - Use the information provided under *Support* for answers

---

## Support

Reach out to me at one of the following places!

- Twitter at [`@wwinvestingllc`](https://twitter.com/wwinvestingllc?lang=en)
- Github at [`seansangh`](https://github.com/seansangh)

---

## Donations (Optional)

- If you appreciate the code provided herein, feel free to donate to the author via [Paypal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=4VED5H2K8Z4TU&source=url).

[<img src="https://www.paypalobjects.com/webstatic/en_US/i/buttons/cc-badges-ppppcmcvdam.png" alt="Pay with PayPal, PayPal Credit or any major credit card" />](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=4VED5H2K8Z4TU&source=url)

---

## License

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)

- **[MIT license](http://opensource.org/licenses/mit-license.php)**
- Copyright 2019 © <a>S.S.</a>
