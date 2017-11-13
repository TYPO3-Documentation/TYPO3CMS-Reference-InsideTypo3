.. include:: ../../../Includes.txt


.. _configuration-default-configuration:

Default configuration
^^^^^^^^^^^^^^^^^^^^^

TYPO3 CMS comes with some default settings, which are defined in
file :file:`typo3/sysext/core/Configuration/DefaultConfiguration.php`.

Here is an extract of that file:

.. code-block:: php

	return [
		'GFX' => [ // Configuration of the image processing features in TYPO3. 'IM' and 'GD' are short for ImageMagick and GD library respectively.
			'thumbnails' => true,
			'thumbnails_png' => true,
			'gif_compress' => true,
			'imagefile_ext' => 'gif,jpg,jpeg,tif,tiff,bmp,pcx,tga,png,pdf,ai,svg',
			...
		],
		...
	];


You will probably find it interesting to take a look at that file,
which also contains values not displayed in the Install Tool and thus
not easily available for modification.
