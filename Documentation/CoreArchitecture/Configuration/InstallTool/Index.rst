.. include:: /Includes.rst.txt


.. _configuration-install-tool:

Install Tool
^^^^^^^^^^^^

The Install Tool provides a convenient user interface for changing
the global configuration. The "All Configuration" view lists all
available options and makes them available for editing.

When changes are saved, the :file:`LocalConfiguration.php` file
is updated.

.. figure:: ../../../Images/ConfigurationInstallTool.png
   :alt: The "All Configuration" view of the Install Tool


Note how the configuration options description is taken from the
inline comments in the :file:`typo3/sysext/core/Configuration/DefaultConfiguration.php`
file. Check out the code again:

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
