# Appendix B: Configuring PHP

; cleaned by the garbage collection process.
; http://php.net/session.gc-maxlifetime
session.gc_maxlifetime = 1440

; NOTE: If you are using the subdirectory option for storing session files
; (see session.save_path above), then garbage collection does *not*
; happen automatically. You will need to do your own garbage
; collection through a shell script, cron entry, or some other method.

; For example, the following script would be the equivalent of
; setting.gc_maxlifetime to 1440 (1440 seconds = 24 minutes);
; /path/to/sessions; find -min +24 xargs rm

PHP 4.2 and less have an undocumented feature that allows you to
; to initialize a session variable in the global scope, when register_globals
; is disabled. PHP 4.3 and later will warn you, if this feature is used.
; You can use the feature and the warning separately. At this time,
; the warning is only displayed, if bug_compat_42 is enabled. This feature
; introduces some ambiguity if not handled correctly. It's
; recommended that you do not use this feature on production servers. But you
; should enable this on development servers and the warning as well. If you
; do not enable the feature on development servers, you won't be warned when it's
; used and debugging errors caused by this can be difficult to track down.

+   - Default Value: On
- Development Value: On
- Production Value: Off
; http://php.net/session.bug_compat-42
session.bug_compat_42 = On

; This setting controls whether or not you are warned by PHP initializing a
; session value into the global space. session.bug_compat_42 must be enabled before
; these warnings can be issued by PHP. See the directive above for more
information.

+   - Default Value: On
- Development Value: On
- Production Value: Off
; http://php.net/session.bug_compat-warn
session.bug_compat_warn = On

; CHECK REFERER to invalidate externally URLs containing ids.
; HTTP_REFERER has to contain this string for the session to be
; considered as valid.
; http://php.net/session.referer_check
session.referer_check =

; How many bytes are read from the file.
; http://php.net/session.entropy-length
session.entropy_length = 0

; Specified here to create the session id.
; http://php.net/session.entropy-file
session.entropy_file = /dev/urandom
session.entropy_file =

; http://php.net/session.entropy-length