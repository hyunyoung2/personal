---
layout: post
title: Test of Code block with highlight in Jekyll
subtitle: This is test for code block in jekyll and Markdown
category: Web Programming
tags: [jekyll, markdown]
permalink: /2016/12/14/How_To_Use_Code_Block_Of_Jekyll/
bigimg: 
  - "/img/Image/BigImages/carmel.jpg" : "Carmel-by-the-Sea, CA (2016)"
---

## How to make code block in Jekyll and Markdown


 > a noraml code block  
 
  ![](/img/Image/WebProgramming/2016-12-14-How_To_Use_Code_Block_Of_Jekyll/1highlight.png)
        
```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* nums, int numsSize, int target) {
    
}
```

## For linenumber, testing any case of using highlighter


  > highlight with linenos

   ![](/img/Image/WebProgramming/2016-12-14-How_To_Use_Code_Block_Of_Jekyll/2highlight.png)

  This way is not comportable when you copy and paste the code, because of linenumber

{% highlight c linenos %}
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* nums, int numsSize, int target) {
    
}
{% endhighlight %}


   > highlight with lineos=table
   
   
   
   ![](/img/Image/WebProgramming/2016-12-14-How_To_Use_Code_Block_Of_Jekyll/3highlight.png)

{% highlight c linenos=table %}
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* nums, int numsSize, int target) {
    
}
{% endhighlight %}

 if you use **lineos=table**, at that time, copy and paste is easy, linenumber doesn't matter. 

 In other words,  
 
 **linenos=table** option is comportable with copy contents, this means when you copy code block, You can select only the code. without linenumber

 you can check [this stackoverflow](http://stackoverflow.com/questions/11093241/how-to-support-line-number-when-using-pygments-with-jekyll)

 **BUT,** after I test that lineos=table and lineos, both options is the same on my gitpage.

  >  highlight with a normal code block

  ![](/img/Image/WebProgramming/2016-12-14-How_To_Use_Code_Block_Of_Jekyll/4highlight.png)

{% highlight c linenos %}
```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* nums, int numsSize, int target) {
    
}
```
{% endhighlight %}


  >  highlight with a normal code block and lineos=table 

   ![](/img/Image/WebProgramming/2016-12-14-How_To_Use_Code_Block_Of_Jekyll/5highlight.png)

{% highlight c linenos=table %}
```c 
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* nums, int numsSize, int target) {
    
}
```
{% endhighlight %}


## Summary of highlight and code block

 I think you don't care aobut if option of highliter is lineos=table or linenos, 
 
 Because in my test both of them is the same. 
 
 > what I recommend
 
 ![](/img/Image/WebProgramming/2016-12-14-How_To_Use_Code_Block_Of_Jekyll/1highlight.png)
 
 > OR
 
 ![](/img/Image/WebProgramming/2016-12-14-How_To_Use_Code_Block_Of_Jekyll/2highlight.png)


## Reference 

  - [StackOverflow](http://stackoverflow.com/questions/11093241/how-to-support-line-number-when-using-pygments-with-jekyll)
  
  - [The Official Liquid Site](https://shopify.github.io/liquid/) Means an open-source template language. 
  
  - [The official Pygments site](http://pygments.org/) is short for Python syntax highlighter.
  
  - [Jekyll git repository](https://github.com/jekyll/jekyll)
  
  - [Github Guide of Markdown Syntax](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)
  
  - [Types of Syntax Highlighter in Markdown](https://support.codebasehq.com/articles/tips-tricks/syntax-highlighting-in-markdown)
