(function ($, window, Drupal) {

    Drupal.behaviors.scrollTopButton = {
      attach: function (context, settings) {

        var button_text = drupalSettings.button_text;
        var button_style = drupalSettings.button_style;
        var button_animation = drupalSettings.button_animation;
        var button_animation_speed = parseInt(drupalSettings.button_animation_speed);
        var scroll_distance = parseInt(drupalSettings.scroll_distance);
        var scroll_speed = parseInt(drupalSettings.scroll_speed);

        var element_name = 'scrollTopButton-' + button_style;

        if (button_style == 'image') {
          button_text = '';
        }

        var $element = $('<a/>', {id: element_name, href: '#', class:'scroll-top-button'});

        if ($('#' + element_name).length === 0) {
          $element.appendTo('body');
        }

        $element.html(button_text);

        var animationIn = 'show';
        var animationOut = 'hide';
        var animationSpeed = 0;
        var buttonVisible = false;

        // set animation for the button
        if (button_animation == 'fade') {
          animationIn = 'fadeIn';
          animationOut = 'fadeOut';
          animationSpeed = button_animation_speed;
        }

        if (button_animation == 'slide') {
          animationIn = 'slideDown';
          animationOut = 'slideUp';
          animationSpeed = button_animation_speed;
        }

        $(window).scroll(function () {
            if ($(window).scrollTop() > scroll_distance) {
                if (!buttonVisible) {
                    $element[animationIn](animationSpeed);
                    buttonVisible = true;
                }
            } else {
                if (buttonVisible) {
                    $element[animationOut](animationSpeed);
                    buttonVisible = false;
                }
            }
        });

        // Scroll to top after click on button
        $element.click(function (event) {
          event.preventDefault();

            $('html, body').animate({ scrollTop: 0}, scroll_speed, 'linear');
        });

      }
    };

  })(jQuery, window, Drupal);
