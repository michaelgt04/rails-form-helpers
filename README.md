# Rails Form Helpers

This is the repo from my clinic today. This should provide you with
working code for the various form helpers that Rails uses. There is
lots of specific syntax that goes into the various types of fields within
the helpers, so be careful. 

Remember, just like many things in coding, you don't have to memorize all of this!
The important thing is that you know how to look at the documentation and
parse through what you need to get the job done!

### Things to Watch Out For

* Make sure your `create` method works!

If your form is not creating the model the right way, a good place to start your
debugging is to test out the logic in your controller's `create` method. Throw a
`pry` in various parts of your code and make sure that you're calling everything
the right way.

* Check your `params`

Check your `params` hash to make sure that everything is getting passed back from
the form the right way. If you see something weird or missing in your `params` hash
chances are, you aren't setting things up exactly correct in the form.

* Use your documentation!

As mentioned in the paragraphs above, your documentation will be a lifesaver with
Rails forms! There is so much specific syntax that you need due to all the Rails
conventions, so get the help you deserve from the documentation! If all else fails,
look back at your code examples as a guide for how to proceed.
