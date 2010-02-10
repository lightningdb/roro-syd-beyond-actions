!SLIDE bullets incremental

# Cells

* Started by Ezra Z
* Packaging code and templates
* Encapsulation
* Reusability
* Nesting

!SLIDE commandline incremental

    $ script/generate cell ShoppingCart display
    create  app/cells/
    create  app/cells/shopping_cart_cell.rb
    create  app/cells/shopping_cart
    create  app/cells/shopping_cart/display.html.erb

!SLIDE ruby

    @@@ ruby
    class ShoppingCartCell < Cell::Base
      def display
        @orders = @opts[:orders]
        render
      end
    end

!SLIDE html

    @@@ html
    <div id="cart">
      You have <%= @orders.size %> in
      your shopping cart.
    </div>

!SLIDE ruby

  File: app/controllers/products_controller.rb

    @@@ ruby
    def show
      @cart = render_cell :shopping_cart,
          :display, :orders => @orders
      render
    end

