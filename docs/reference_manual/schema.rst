.. _SiliconCompiler Schema:

Schema
=====================

Keywords
---------

.. glossary::
   default
       Reserved SiliconCompiler schema key that can be replaced by any legal string.

Parameter Fields
-----------------

.. glossary::

   author
       File author. The author string records the person/entity that authored/created each item in the list of files within 'value' parameter field. The 'author' field can be used to validate the provenance of the data used for compilation.

   date
       String containing the data stamp of each item in the list of files within 'value' parameter field. The 'date' field can be used to validate the provenance of the data used for compilation.

   defvalue
       Default value for the parameter. The default value must agree with the parameter 'type'. To specify that a parameter has no default value, set the defvalue to [] (ie empty list) for a list type and to 'null' or None for a non-list/scalar type.

   example
       List of two strings, the first string containing an example for specifying the parameter using a command line switch, and a second string for setting the value using the core Python API. The examples can be pruned/filtered before the schema is dumped into a JSON file.

   hashalgo
       Hasing algorithm useed to calculate filehash value.

   filehash
       Calculated file hash value for each file in the 'value' field of the parameter.

   help
       Complete parameter help doc string. The help string serves as ground truth for describing the parameter functionality and should be used for long help descriptions in command line interface programs and for automated schema document generation. The long help can be pruned/filtered before the schema is dumped into a JSON file.

   lock
       Boolean value dictating whether the parameter can be modified by the set/get/add core API methods. A value of True specifiers that the parameter is locked and cannot be modified. Attempts to write to to a locked parameter shall result in an exception/error that blocks compilation progress.

   require
       String that specifies scenarios, conditions, and modes for which the parameter must return a non-empty value. Valid requirement keywords include 'all' and 'fpga'/'asic'. The 'all' keyword specifies that the parameter must always have a non-empty value before running a flow. The 'fpga'/'asic' keyword specifies that that the parameter must have a non-empty value when the respective mode is being executed.  All Boolean values have a valid True/False default value and a requirement of 'all'.  The vast majority of schema parameters have requirements of None and empty values which can be overriden by the user based on need.

   signature
       String recording a unique machine calculated string for each item in the list of files within 'value' parameter field. The 'signature' field can be used to validate the provenance of the data used for compilation.

   switch
       String that specifies the equivalent switch to use in command line interfaces. The switch string must start with a '-' and cannot contain spaces.

   shorthelp
       Short help string to be used in cases where brevity matters. Use cases include JSON dictionary dumps and command line interface help functions.

   type
       The parameter type. Supported types include Python compatible types ('int', 'float', and 'bool') and two custom file types ('file' and 'dir'). The 'file' and 'dir' type specify that the parameter is a 'regular' file or directory as described by Posix. All types except for the 'bool' types can be specified as a Python compatible list type by enclosing the type value in brackets. (ie. [str] specifies that the parameter is a list of strings). Additionally strings, integers, and floats can be tagged as tuples, using the Python parentheses like syntax (eg. [(float,float)] specifies a list of 2-float tuples). Input arguments and return values of the set/get/add core methods are encoded as native Python types. The JSON format does not natively support all of these data types, so to ensure platform interoperability, all SC schema parameters are converted to strings before being exported to a json file. Additionally, note that the parameter value 'None' gets translated to the "null", True gets translated to "true", and False gets translated to "false" before JSON export.



Parameters
----------

.. schemagen::
