+   -Dropped .radio-inline and .checkbox-inline.
+   -Replaced .has-error, .has-warning, and .has-success classes with HTML5 form validation via CSS‘s :invalid and :valid pseudo-classes.

# Buttons

+   -Renamed .btn-default to .btn-secondary.
+   -Change buttons' [disabled] to :disabled
+   -Removed explicit spacing between button groups in button toolbars

# Panels

+   -.panel to .card, now built with flexbox.
+   -.panel-default removed and no replacement.
+   -.panel-group removed and no replacement.
+   -.panel-heading to .card-header
+   -.panel-title to .card-title.
+   -.panel-body to .card-body
+   -.panel-footer to .card-footer
+   -.panel-primary, .panel-success, .panel-info, .panel-warning, and .panel-danger have been dropped for .bg-, .text-, and .border utilities generated from our $theme-colors Sass map.