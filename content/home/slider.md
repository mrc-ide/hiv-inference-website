+++
# Slider widget.
widget = "slider"  # See https://sourcethemes.com/academic/docs/page-builder/
headless = true  # This file represents a page section.
active = false  # Activate this widget? true/false
weight = 1  # Order that this section will appear.

# Slide interval.
# Use `false` to disable animation or enter a time in ms, e.g. `5000` (5s).
interval = 5000

# Slide height (optional).
# E.g. `500px` for 500 pixels or `calc(100vh - 70px)` for full screen.
height = "250px"

# Slides.
# Duplicate an `[[item]]` block to add more slides.
[[item]]
  title = "EPPASM"
  content = "Epidemic Projection Package - Age/Sex Model"
  align = "left"  # Choose `center`, `left`, or `right`.

  # Overlay a color or image (optional).
  #   Deactivate an option by commenting out the line, prefixing it with `#`.
  overlay_color = "#2b94c3"  # An HTML color value.
  # overlay_img = "headers/bubbles-wide.jpg"  # Image path relative to your `static/media/` folder.
  overlay_filter = 0.1  # Darken the image. Value in range 0-1.

  # Call to action button (optional).
  #   Activate the button by specifying a URL and button label below.
  #   Deactivate by commenting out parameters, prefixing lines with `#`.
  cta_label = "Get EPPASM"
  cta_url = "https://github.com/mrc-ide/eppasm"
  cta_icon_pack = "fas"
  cta_icon = "virus-slash"

[[item]]
  title = "Naomi"
  content = " Naomi model for subnational HIV estimation"
  align = "left"

  overlay_color = "#2b94c3"  # An HTML color value.
  # overlay_img = "headers/bubbles-wide.jpg"
  overlay_filter = 0.5  # Darken the image. Value in range 0-1.

  cta_label = "Get Naomi"
  cta_url = "https://github.com/mrc-ide/naomi"
  cta_icon_pack = "fas"
  cta_icon = "virus-slash"

[[item]]
  title = "Projects"
  content = "current running projects"
  align = "left"

  overlay_color = "#2b94c3"  # An HTML color value.
  # overlay_img = "headers/project.png"
  overlay_filter = 0.2  # Darken the image. Value in range 0-1.

  cta_label = "Check out"
  cta_url = "/project/"
  cta_icon_pack = "fas"
  cta_icon = "virus-slash"
+++
