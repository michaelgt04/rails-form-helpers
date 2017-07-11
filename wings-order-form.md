# Wings Order

We have successfully created an application to create delicious wing orders of various flavors!

## Application Set Up
Set up the application and run the test suite with the following commands:

```no-highlight
bundle install
rake db:create
rake db:migrate
rake db:seed
rake
```
The tests should be passing, and the form should be working correctly.

## Refactor the wing order form

However, we did not use [Rails Form Helpers][rails-form-helpers], so the HTML that makes up our form is starting to become excessive and difficult to understand.
Let's refactor the form to use the appropriate rails form helpers to reduce the html clutter.

Refactor the form in `wing_orders/new.html.erb` to user Rails form helpers. Understanding and knowing your way around the Rails documentation is an important skill to learn. Look into the following resources for guidance:
- [Select and Option Tags][select-and-option-tags]
- [Collection Radio Buttons][collection-radio-buttons]
- [Check Boxes][check-boxes]
- [Collection Check Boxes][collection-check-boxes]

[rails-form-helpers]: http://guides.rubyonrails.org/form_helpers.html
[select-and-option-tags]: http://guides.rubyonrails.org/form_helpers.html#the-select-and-option-tags
[collection-radio-buttons]: http://edgeapi.rubyonrails.org/classes/ActionView/Helpers/FormOptionsHelper.html#method-i-collection_radio_buttons
[check-boxes]: http://guides.rubyonrails.org/form_helpers.html#checkboxes
[collection-check-boxes]: http://edgeapi.rubyonrails.org/classes/ActionView/Helpers/FormOptionsHelper.html#method-i-collection_check_boxes

Once your are finished refactoring the form, run `rake` to ensure that the original functionality still works.

## Render forms in a partial

It would be nice if we could edit our orders in case we forgot to add ranch dressing! Write an acceptance test and implement functionality for editing a wing order. Leverage the same form helper we created by creating a partial for the form and rendering it in two places.

## Tips

You'll notice that the collection documentation has the following code for general usage:

`collection_radio_buttons(object, method, collection, value_method, text_method, ...)`

and the following code for example usage:

`collection_radio_buttons(:post, :author_id, Author.all, :id, :name_with_initial)`.

Dissecting this, the object is what the form is creating. In the example, we are creating a post object. If we were to use the `form_for` helper with `form_for(post) do |f|`, we could replace the example code with the following:

`f.collection_radio_buttons(:author_id, Author.all, :id, :name_with_initial)`

since the radio buttons are now pointing directly to the post object.

The `method` (in this case `:author_id`) is referring to the column of the object to which this portion of the form is posting.

The `collection` is the collection of objects that the user can choose from. In this case, it is an array of `Author` objects.

The `value_method` is the method called on a single Author object in order to determine what value is passed through to params when the form is submitted. In this case, when we select a single `Author` and submit, `:id` is pulling the id of that specific author and passing it as a parameter. If we were to check the params hash, we would see the value of the id stored in `params[:post][:author_id]`.

The `text_method` is the method called on the on a single Author object in order to determine how each selection will be displayed in the client. In the example, we wish to have the user select from a list of Author names, not a list of Author id's, but the id of the Author is what gets submitted through the `value_method`.
