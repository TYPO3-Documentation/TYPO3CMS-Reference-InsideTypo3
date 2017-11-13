.. include:: ../../../Includes.txt


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
values in the :file:`typo3/sysext/core/Configuration/DefaultConfigurationDescription.php`
file. Check out the code of the :file:`DefaultConfiguration` and the matching description:

.. code-block:: php

   return [
      'GFX' => [ // Configuration of the image processing features in TYPO3. 'IM' and 'GD' are short for ImageMagick and GD library respectively.
         'thumbnails' => 'Boolean: Enables the use of thumbnails in the backend interface.',
         'thumbnails_png' => 'Boolean. If false, thumbnails from non-image files will be converted to \'gif\', otherwise \'png\' (default).',
         'gif_compress' => 'Boolean: Enables the use of the <code>\\TYPO3\\CMS\\Core\\Utility\\GeneralUtility::gifCompress()</code> workaround function for compressing giffiles made with GD or IM, which probably use only RLE or no compression at all.',
         'imagefile_ext' => 'Commalist of file extensions perceived as images by TYPO3. List should be set to \'gif,png,jpeg,jpg\' if IM is not available. Lowercase and no spaces between!',
         // ...
      ],
      // ...
   ];

   return [
      'GFX' => [ // Configuration of the image processing features in TYPO3. 'IM' and 'GD' are short for ImageMagick and GD library respectively.
         'thumbnails' => true,
         'thumbnails_png' => true,
         'gif_compress' => true,
         'imagefile_ext' => 'gif,jpg,jpeg,tif,tiff,bmp,pcx,tga,png,pdf,ai,svg',
         // ...
      ],
      // ...
   ];