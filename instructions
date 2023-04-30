Integrate select2 for the JetFormbuilder, Elementor, and JetSmartFilter
Offical site: https://select2.org/

JETFORMBUILDER VERSION

1, First step we need select2. You don't need to install it at the file level, it's enough to use some kind of cdn link:

<link href="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/css/select2.min.css" rel="stylesheet" />
<script src="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/js/select2.min.js"></script>

Additional information. The default language of Select2 is English, but due to its popularity it has been translated into many languages. 
If you need it, you can find all the languages currently available on the following page: https://cdn.jsdelivr.net/npm/select2@4.0.13/dist/js/i18n/

Just place the link you have chosen under the installation links in the first step, for example in the Spanish language case this will be the link:
https://cdn.jsdelivr.net/npm/select2@4.0.13/dist/js/i18n/es.js


Before proceeding to the second step, the target select element is needed for iniciliation, which in this case will always be the jetFormbuilder field name.
See the example image below if you don't understand:

https://prnt.sc/NcdPFrG6p32L

There are several ways to place the code, use a built-in solution from the Elementor (pro required):
Navigate to the
Elementor - Custom Code and create a new one.

Now copy and paste the following codes(if you need the language file, you can use it as I showed above):

<link href="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/css/select2.min.css" rel="stylesheet" />
<script src="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/js/select2.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/select2@4.0.13/dist/js/i18n/en.js"></script>


2, The second step will be initialisation
Don't forget to replace my field name with yours(#city_selector).
Now it's time for inicilisation, without parameters for now:


<script>
	jQuery(document).ready(function($) {
  $("#city_selector").select2({  	
    });
});

</script>


3, The third step will be parameterisation.
Select2 can be supplied with several parameters. By default, you get a search box that reacts to the content within the select elements. 

Disable the search function: minimumResultsForSearch: Infinity

If you go back to the search function, there are some related parameters. For example, the minimum number of carats, or the maximum, 
or the number of results to display. You can find all these on the documentation page here:

https://select2.org/searching

How does it look if we have placed several parameters in the code? 
Here is a complete example:


<link href="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/css/select2.min.css" rel="stylesheet" />
<script src="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/js/select2.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/select2@4.0.13/dist/js/i18n/en.js"></script> 

<script>
	jQuery(document).ready(function($) {
  $("#city_selector").select2({  	
		minimumInputLength: 3,
		maximumInputLength: 10,
		minimumResultsForSearch: 5
    });
});

</script>


4, Multiselect
Select2 will know if it's a select that is multiple based, so you basically don't need to add to the code (by default)

However, unlike single, with multi select you have to exclude the viewfinder a little differently if you don't need it:
// Exclude the search box

jQuery(document).ready(function($) {
  $("#city_selector").select2();
  
  $('#city_selector').on('select2:opening select2:closing', function( event ) {
    var $searchfield = $(this).parent().find('.select2-search__field');
    $searchfield.prop('disabled', true);
  });
});


Since select contains a generated placeholder by default and includes it, if you want to remove it, define the placeholder by default and then exclude it:
It is important to remove the placeholder text in the jetformbuilder if you have left it in!
jQuery(document).ready(function($) {
  $("#city_selector").select2({
    placeholder: "Select a city",
    allowClear: true
  });
  
  $('#city_selector').on('select2:opening select2:closing', function( event ) {
    var $searchfield = $(this).parent().find('.select2-search__field');
    $searchfield.prop('disabled', true);
  });
  
  
5, Additions parameters:

  The good news is that you can limit how much they can select with the following parameter:
  maximumSelectionLength: 3
  
  
  So the whole code will look something like this:
  
  <script>
jQuery(document).ready(function($) {
  $("#city_selector").select2({
    placeholder: "Válassz egy várost",
    allowClear: true,
		maximumSelectionLength: 3 // number of selected item maximum
  });
  
  $('#city_selector').on('select2:opening select2:closing', function( event ) {
    var $searchfield = $(this).parent().find('.select2-search__field');
    $searchfield.prop('disabled', true);
  });
});
</script>


------

6, Code structure, and multiple select field select2 conversion:
Let's look at an example where 3 select re's are connected to select2. 
From this you will know later on how to connect more in the right structure and parameterize them:



<link href="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/css/select2.min.css" rel="stylesheet" />
<script src="https://cdn.jsdelivr.net/npm/select2@4.1.0-rc.0/dist/js/select2.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/select2@4.0.13/dist/js/i18n/en.js"></script> 

<script>


jQuery(document).ready(function($) {
	 // remove th empty items
  // First select item
  $('#city_selector option[value=""]').remove();
  $("#city_selector").select2({
    placeholder: "Válassz egy várost",
    allowClear: false,
		maximumSelectionLength: 3,
		
  });
  
  $('#city_selector').on('select2:opening select2:closing', function( event ) {
    var $searchfield = $(this).parent().find('.select2-search__field');
    $searchfield.prop('disabled', true);
  });
	// Second select item
	$('#manual_selection_my').select2({
	// place here your paramteres if need
	minimumResultsForSearch: Infinity 
	});
	// Third select item
	$('#wp_posts').select2({
	// place here your paramteres if need
});
});

</script>




FAQ

1. Bad dropdown results, place empty items in the multiselect:


For example, if you are using the JetEngine glossary with a lot of elements, and your file has some empty elements in it when importing it,
and you get the following error (image): https://prnt.sc/PlqltmwHU0xX


The following code will remove the empty items from the select.
// remove the empty items
$('#city_selector option[value=""]').remove();


2. How can i disable the select2 on mobile?

jQuery(document).ready(function($) {
		$('#wp_posts').select2({
	});
 if ( /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent) ) {
 $("#wp_posts").select2('destroy');
}
 });	

3. Can I create a hierarchical display?

Select2 supports it but JFB doesn't, so it would be a real pain to do this.

4. Is this select2 compatible with the Save Form Progress system?

Yes.

Can i make my custom design?
Of course, unlike the traditional browser-rendered select field, you can customize any part of select2 to your liking. 
You will find all classes. Use devtools to find the classes.

I suggest, if you are using Elementor custom code, that you open a new tag in the same place where you define select2:

<style>
.select2-container--default .select2-results>.select2-results__options {
	color: black;
	}
</style>

Write this under the script tags, so you have the select2 jquery code and your stylistic code in one place.

5. Could I put some kind of icon in front of each element, maybe?
Yes, this is called a template, here is a JFB compatible example:
This puts a + icon in front of each option.

jQuery(document).ready(function($) {
// basic FA template

var template = function(state) {
  if (!state.id) {
    return state.text;
  }
  else {
    var icon = $('<span><i class="fa fa-plus"></i></span>');
    var text = $('<span>' + state.text + '</span>');
    var result = $('<span></span>');
    result.append(icon).append(text);
    return result;
  }
}

  $('#manual_selection_my').select2({
    templateResult: template,
    minimumResultsForSearch: Infinity 
  });
});


