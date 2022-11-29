[[ReadItLater]] [[Article]]

# [Why do browsers match CSS selectors from right to left ? - GeeksforGeeks](https://www.geeksforgeeks.org/why-do-browsers-match-css-selectors-from-right-to-left/)

[**C**ascading **S**tyle **S**heets](https://www.geeksforgeeks.org/css/) fondly referred to as CSS, is a simply designed language intended to simplify the process of making web pages presentable. CSS allows you to apply styles to web pages. More importantly, CSS enables you to do this independent of the HTML that makes up each web page. It describes how a webpage should look: it prescribes colors, fonts, spacing, and much more. In short, you can make your website look however you want. CSS lets developers and designers define how it behaves, including how elements are positioned in the browser. 

In this article, we will learn why browsers match CSS selectors from right to left. 

**Why do browsers match CSS selectors from right to left?**

[[nav]] ul li {...}    

 **Note:**  The browser will read from   li -> ul -> [[nav]]

The browser match CSS selectors from the right to left because it gives an obvious starting point and lets you get rid of most of the candidate selectors very quickly.

If the browser will render from the left side then there are more chances that if the class/id/element-name is not correct or you forget to use’ #’ for id and ‘.’ for class, then the browser will not even try to read the remaining data. On the other hand, if it renders from the right side then the browser will try to fetch the data. 

**Example 1:** In the below code, the browser will pick the CSS selector from right to left. First, it will search all **<span>** tags from the browser then it will make a search for the [**<h1>**](https://www.geeksforgeeks.org/html-h1-to-h6-align-attribute/) tag then, in the end, it will look for the [**<div>**](https://www.geeksforgeeks.org/div-tag-html/) tag.

## HTML

`<!DOCTYPE html>`

`<``html``>`

`<!DOCTYPE html>`

`<``html``>`

`<``head``>`

    `<``style``>`

        `div h1 span {`

            `color: green;`

        `}`

    `</``style``>`

`</``head``>`

`<``body``>`

    `<``center``>`

        `<``h2` `style``=``"color:green"``>GeeksforGeeks</``h2``>`

        `<``b``>`

`<``p``>Right to left selectors</``p``>`

`</``b``>`

        `<``div``>`

            `This is div`

            `<``h1``>`

                `This is h1 tag<``br` `/>`

                `<``span``>`

                    `This is span tag`

                `</``span``>`

            `</``h1``>`

        `</``div``>`

        `<``span``>`

            `This is span outside div`

        `</``span``>`

    `</``center``>`

`</``body``>`

`</``html``>`

`<``head``>`   

    `<``style``>`

        `div h1 span{`

            `color:green;`

        `}`

    `</``style``>`

`</``head``>`

`<``body``>`

    `<``center``>`

        `<``h2` `style``=``"color:green"``>GeeksforGeeks</``h2``>`

        `<``b``>`

`<``p``>Right to left selectors</``p``>`

`</``b``>`

        `<``div``>`

            `This is div`

            `<``h1``>`

               `This is h1 tag<``br``/>`

                `<``span``>`

                    `This is span tag`

                `</``span``>`

            `</``h1``>`

        `</``div``>`

        `<``span``>`

           `This is span outside div`

        `</``span``>`       

    `</``center``>`

`</``body``>`

`</``html``>`               

**Output:** 

![](https://media.geeksforgeeks.org/wp-content/uploads/20220614120703/righttoleft.png)

**Example 2:** In the below code, the browser will pick the CSS selector from right to left. First, it will search all [**<b>**](https://www.geeksforgeeks.org/html-b-tag/) tags from the browser, then it will search for the [**<span>**](https://www.geeksforgeeks.org/html-span-tag/) tag then, in the end, it will look for the [**<div>**](https://www.geeksforgeeks.org/div-tag-html/) tag.

## HTML

`<!DOCTYPE html>`

`<``html``>`

`<``head``>`

    `<``style``>`

        `div span b {`

            `color: green;`

        `}`

        `span {`

            `font-size: 40px;`

        `}`

        `body {`

            `background-color: lightgrey;`

        `}`

    `</``style``>`

`</``head``>`

`<``body``>`

    `<``center``>`

        `<``div``>`

            `<``span``>`

                `<``b``> GeeksforGeeks </``b``>`

            `</``span``>`

        `</``div``>`

        `<``h2``>A computer science portal for geeks</``h2``>`

    `</``center``>`

`</``body``>`

`</``html``>`

**Output:**

![](https://media.geeksforgeeks.org/wp-content/uploads/20220614120324/righttoleft2.png)