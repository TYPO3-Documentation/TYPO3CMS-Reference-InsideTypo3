.. include:: /Includes.rst.txt


.. _configuration-default-configuration:

Default configuration
^^^^^^^^^^^^^^^^^^^^^

TYPO3 CMS comes with some default settings, which are defined in
file :file:`typo3/sysext/core/Configuration/DefaultConfiguration.php`.

Here is an extract of that file:

.. code-block:: php

	return array(
		'GFX' => array(
			// Configuration of the image processing features in TYPO3. 'IM' and 'GD' are short for ImageMagick and GD library respectively.
			'image_processing' => true,                        // Boolean: Enables image processing features. Disabling this means NO image processing with either GD or IM!
			'thumbnails' => true,                            // Boolean: Enables the use of thumbnails in the backend interface.
			'thumbnails_png' => 0,                            // Bits. Bit0: If set, thumbnails from non-jpegs will be 'png', otherwise 'gif' (0=gif/1=png). Bit1: Even JPG's will be converted to png or gif (2=gif/3=png)
			'gif_compress' => true,                            // Boolean: Enables the use of the \TYPO3\CMS\Core\Utility\GeneralUtility::gifCompress() workaround function for compressing giffiles made with GD or IM, which probably use only RLE or no compression at all.
			...
		),
		...
	);


You will probably find it interesting to take a look at that file,
which also contains values not displayed in the Install Tool and thus
not easily available for modification.
