!SLIDE bullets incremental

# Apotomo

* event driven widgets
* stateful component tree
* event bubbling
* form_to_event
* testing

!SLIDE ruby

    @@@ruby
    class CounterCell < Apotomo::StatefulWidget
      transition :from => :display,
          :to => :increment

      def display
        respond_to_event :counterClick,
            :with => :increment

        @count = 0
        render # renders display.html.erb
      end

      def increment
        # @count is stateful
        @count += 1
        render :view => :display
      end
    end

!SLIDE ruby

    @@@ ruby
    class ExistingController
        < ApplicationController
      include Apotomo::ControllerHelper

      def some_action
        # do what you want...

        use_widgets do |root|
          root << cell(:counter, :display,
            'my_first_counter')
        end
      end
    end

!SLIDE html

    @@@ html
    <!-- I'm some_action.html.erb -->
    <%= render_widget 'my_first_counter' %>

