# TABLE F-20 XPAT XML FUNCTIONS (Continued)

| Function | Return Value | Action |
| :--- | :--- | :--- |
| xml_set_object(int pind, object &obj) | int | Sets up an object that should be used for callbacks |
| xml_set_element_handler(int pind, string hdl1, string ehdl) | int | Sets up start and end element handlers |
| xml_set_character_data_handler(int pind, string hdl) | int | Sets up a character-data handler |
| xml_set_processing_instruction_handler(int pind, string hdl) | int | Sets up a processing-instruction (Pi) handler |
| xml_set_default_handler(int pind, string hdl) | int | Sets up a default handler |
| xml_set_unparsed_entity_decl_handler(int pind, string hdl) | int | Sets up an unparsed-entity-declaration handler |
| xml_set_notation_decl_handler(int pind, string hdl) | int | Sets up a notation-declaration handler |
| xml_set_external_entity_ref_handler(int pind, string hdl) | int | Sets up an external entity-reference handler |
| xml_set_start_namespace_decl_handler(int pind, string hdl) | int | Sets up a character-data handler |
| xml_set_end_namespace_decl_handler(int pind, string hdl) | int | Sets up a character-data handler |
| xml_parse(int pind, string data [, int isFinal]) | int | Starts parsing an XML document |
| xml_parse_into_struct(int pind, string data, array &struct, array &index) | int | Parsing a XML document |
| xml_get_error_code(int pind) | int | Gets XML parser-error code |
| xml_error_string(int code) | string | Gets XML parser-error string |
| xml_get_current_line_number(int pind) | int | Gets the current line number for an XML parser |
| xml_get_current_column_number(int pind) | int | Gets the current column number for an XML parser |