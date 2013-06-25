# Agregando tu modulo a la guia de usuario

Hacer que tu modulo trabaje con la guia de usuario es simple.

Primero, copia esta configuración y colocalo en `<module>/config/userguide.php`, remplaza los campos en `<>` con los apropiados valores:

	return array
	(
		// Leave this alone
		'modules' => array(
	
			// This should be the path to this modules userguide pages, without the 'guide/'. Ex: '/guide/modulename/' would be 'modulename'
			'<modulename>' => array(
	
				// Whether this modules userguide pages should be shown
				'enabled' => TRUE,
				
				// The name that should show up on the userguide index page
				'name' => '<Module Name>',
	
				// A short description of this module, shown on the index page
				'description' => '<Description goes here.>',
				
				// Copyright message, shown in the footer for this module
				'copyright' => '&copy; 2010–2011 <Your Name>',
			)	
		),

		/*
		 * If you use transparent extension outside the Kohana_ namespace,
		 * add your class prefix here. Both common Kohana naming conventions are
		 * excluded: 
		 *   - Modulename extends Modulename_Core
		 *   - Foo extends Modulename_Foo
		 * 
		 * For example, if you use Modulename_<class_name> for your base classes
		 * then you would define:
		 */
		'transparent_prefixes' => array(
			'Modulename' => TRUE,
		)
	);

Siguiente, crea un folder en tu directorio module llamado `guide/<modulename>` y crea `index.md` y `menu.md`. Todas las pagina de la guia de usuario usan [Markdown](markdown). La archivo index es el que se mostrara en el index de tu modulo, el archivo menu es el que se mostrara en la columna lateral. El menu debera ser formateado de la siguiente manera:

	## [Module Name]()
	 - [Page name](page-path)
	 - [This is a Category](category)
		 - [Sub Page](category/sub-page)
		 - [Another](category/another)
			 - [Sub sub page](category/another/sub-page)
	 - Categories do not have to be a link to a page
		 - [Etcetera](etc)

Las rutas de las paginas son relativas a `guide/<modulename>`.  Entonces `[Page name](path-path)` se vera `guide/<modulename>/page-name.md` y `[Another](category/another)` se vera `guide/<modulename>/page-name.md`.   The guide pages can be named or arranged any way you want within that folder (with the exception of `menu.md` and `index.md`). The breadcrumbs and page titles are pulled from the `menu.md file`, not the file names or paths.  You can have items that are not pages (a category that doesn't have a corresponding page).  To link to the `index.md` page, you should have an empty link, e.g. `[Module Name]()`.  Do not include `.md` in your links.  
