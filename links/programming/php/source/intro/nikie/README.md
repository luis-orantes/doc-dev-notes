
### Understanding PHP's internal function definitions

This article walks PHP developers through how to locate and understand the definitions of PHP’s internal C functions—like strpos and strlen—by examining the PHP 5.4 source.
It shows the difference between declarations (typically found in .h header files under ext/standard/) and the actual implementations (in .c files), explains the common structure of internal functions—including variable declarations, parameter parsing via zend_parse_parameters(), type specifiers (e.g. "sz|l"), error handling, logic branching, and return macros like RETURN_LONG or RETURN_FALSE—and briefly distinguishes between functions defined in extensions (PHP_FUNCTION) versus those built into the Zend engine itself (ZEND_FUNCTION). 

https://www.npopov.com/2012/03/16/Understanding-PHPs-internal-function-definitions.html
