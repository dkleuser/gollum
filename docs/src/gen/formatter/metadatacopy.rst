.. Autogenerated by Gollum RST generator (docs/generator/*.go)

MetadataCopy
============

This formatter sets metadata fields by copying data from the message's
payload or from other metadata fields.




Parameters
----------

**CopyToKeys**

  A list of meta data keys to copy the payload or metadata
  content to.
  By default this parameter is set to an empty list.
  
  

Parameters (from core.SimpleFormatter)
--------------------------------------

**ApplyTo**

  This value chooses the part of the message the formatting
  should be applied to. Use "" to target the message payload; other values
  specify the name of a metadata field to target.
  By default this parameter is set to "".
  
  

**SkipIfEmpty**

  When set to true, this formatter will not be applied to data
  that is empty or - in case of metadata - not existing.
  By default this parameter is set to false
  
  

Examples
--------

This example copies the payload to the fields prefix and key. The prefix
field will extract everything up to the first space as hostname, the key
field will contain a hash over the complete payload.

.. code-block:: yaml

	 exampleConsumer:
	   Type: consumer.Console
	   Streams: "*"
	   Modulators:
	     - format.MetadataCopy:
	       CopyToKeys: ["prefix", "key"]
	     - format.SplitPick:
	       ApplyTo: prefix
	       Delimiter: " "
	       Index: 0
	     - formatter.Identifier
	       Generator: hash
	       ApplyTo: key





