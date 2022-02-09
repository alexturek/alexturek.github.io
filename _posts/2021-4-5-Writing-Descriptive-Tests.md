_Originally published as an internal Github Gist with Ahmed Owainati Jan 2017. Later presented with some silly slides with Ian Macleod Sep 2017._

The goal of testing code is both

1. Document what the code should do
2. Assert that it does it

It's very common to find test that do (2) but neglect (1).

If tests are hard to read, it has the same effect as code that's hard to read. The harder something is to understand, the harder it is to trust. The less you trust code, the harder it is to change.

## Testing strategy

This is why I write the skeleton of my tests before I implement them. As an example:

    ShoppingCart.checkout()
      when the cart is empty
        throws an EmptyCartError
        does not place an order
      when the user doesn't have a credit card
        asks for a credit card
      creates an order with every item
      sends a confirmation email
      empties the cart afterwards

When flattened down to sentences, they're understandable to someone unfamiliar with the code.

    ShoppingCart.checkout() when the cart is empty throws an EmptyCartError
    ShoppingCart.checkout() when the cart is empty does not place an order
    ShoppingCart.checkout() when the user doesn't have a credit card asks for a credit card
    ShoppingCart.checkout() creates an order with every item
    ShoppingCart.checkout() sends a confirmation email
    ShoppingCart.checkout() empties the cart afterwards

Each sentence fits the structure

1. **subject**
2. **{possibly context}**
3. **verbs a noun**

This is how BDD-style (`describe`, `context`, `it`) spec frameworks are designed to be used. "`it`" always refers to the **subject** in the parent `describe` block.

## Common Problems

### It `does the right thing`, with lots of assertions

Scenario: I'm working on a system, changing some account setup code, and I just broke this test

    ShoppingCart.checkout() does the right thing

I've never worked in the ShoppingCart code before. I don't know what `the right thing` is. What did I break?

To answer this question, I have to read the entire test implementation, including setup code. And a test with this name almost certainly has several `assert`s inside of it. I may have to go find someone who knows what the right thing is, or debug the entire feature. And the bug might be in the code-under-test, or the test itself. Sometimes, this could be a bug in the test, or it could be an assertion of a behavior that _is not longer `the right thing`_. It's going to be hard for me to find this out without getting a lot more context.

#### The fix - specific `it` blocks with very few assertions

Now imagine the test is instead named

    ShoppingCart.checkout() sends a confirmation email

Okay, I know what I'm going to find in this test. I'm going to see a call to `ShoppingCart.checkout()`, followed by some sort of assertion that an email was sent. I can very quickly identify whether the assertion matches the description. If it does, then I can assume the test works, and I've broken a very specific part of the implementation. This narrows down my total search space.

**Specific tests are easier to read than vague tests.**

### Awkward English heirarchies

Our test heirarchy from above could be "completed" like this:

    ShoppingCart.checkout()
      when the cart is empty
        throws an EmptyCartError
        does not place an order
      when the cart has items
        when the user doesn't have a credit card
          asks for a credit card
        when the user has a credit card
          creates an order with every item
          sends a confirmation email
          empties the cart afterwards

Unwinding these to English sentences, we get some really awkward test descriptions

      ShoppingCart.checkout() when the cart is empty throws an EmptyCartError
      ShoppingCart.checkout() when the cart is empty does not place an order
      ShoppingCart.checkout() when the cart has items when the user doesn't have a credit card asks for a credit card
      ShoppingCart.checkout() when the cart has items when the user has a credit card creates an order with every item
      ShoppingCart.checkout() when the cart has items when the user has a credit card sends a confirmation email
      ShoppingCart.checkout() when the cart has items when the user has a credit card empties the cart afterwards

The other drawback here is that, as someone coming along later and reading these tests, I have to scan deeply and maintain more context in my head to figure out what's happening in a specific `it` block. Be nicer to the reader

#### The fix - Assume happy path context, and test exceptional cases in their own contexts

If you think of the "normal" case as the user has everything required to successfully check out, then you can flatten these tests, and incidentally make the test descriptions much easier to read and reason about.

    // beforeEach:
    //  1. make sure the user has a credit card
    //  2. make sure there's some items in the cart
    ShoppingCart.checkout()
      // beforeEach: empty the cart
      when the cart is empty
        throws an EmptyCartError
        does not place an order
      // beforeEach: remove the credit card
      when the user doesn't have a credit card
        asks for a credit card
      creates an order with every item
      sends a confirmation email
      empties the cart afterwards

**Flatter tests are easier to read than nested tests.**
