# Built-In Events

Many of symfony's classes have built-in events, allowing you to extend the framework without necessarily changing the classes themselves. Table 17-1 lists these events, together with their types and arguments.

Table 17-1 - Symfony's Events

| Event name (Type) | Notifiers | Arguments |
| :--- | :--- | :--- |
| application.log (notify) | lot of classes | priority |
| application.throw_exception (notifyUntil) | sfException | - |
| autoload.filter_config (filter) | sfAutoloadConfigHandler | - |
| command.log (notify) | sfCommand* classes | priority |
| command.pre_command (notifyUntil) | sfTask | arguments, options |
| command.post_command (notify) | sfTask | - |
| command.filter_options (filter) | sfTask | command_manager |
| configuration.method_not_found (notifyUntil) | sfProjectConfiguration | method, arguments |
| component.method_not_found (notifyUntil) | sfComponent | method, arguments |
| context.load_factories (notify) | sfContext | - |
| context.method_not_found (notifyUntil) | sfContext | method, arguments |
| controller.change_action (notify) | sfController | module, action |
| controller.method_not_found (notifyUntil) | sfController | method, arguments |
| controller.page_not_found (notify) | sfController | module, action |
| debug.web.load_panels (notify) | sfWebDebug | - |
| debug.web.view.filter_parameter_html (filter) | sfWebDebugPanelView | parameter |
| doctrine.configure (notify) | sfDoctrinePluginConfiguration | - |
| doctrine.filter_model_builder_options (filter) | sfDoctrinePluginConfiguration | - |
| doctrine.filter_cli_config (filter) | sfDoctrinePluginConfiguration | - |
| doctrine.configure_connection (notify) | Doctrine_Manager | connection, database |
| doctrine.admin.delete_object (notify) | - | object |
| doctrine.admin.save_object (notify) | - | object |
| doctrine.admin.build_query (filter) | - | |
| doctrine.admin.pre_execute (notify) | - | configuration |
| form.post_configure (notify) | sfFormSymfony | - |
| form.filter_values (filter) | sfFormSymfony | - |
| form.validation_error (notify) | sfFormSymfony | error |
| form.method_not_found (notifyUntil) | sfFormSymfony | method, arguments |
| mailer.configure (notify) | sfMailer | - |