# jQuery minLight lightbox plugin

minLight is meant to create the most common, simple lightboxes that use a customizable fading animation.


## Usage

	$(".minlight-links").minLight({
		container: "#main",
		onOpen: function() {
			// context is the lightbox the link has opened
			console.log( this ); // <div class="lightbox"></div>
		}
	});


## Options

All options can be overridden by passing an object literal like any other plugin,<br>
with the `"option"` method,<br>
OR with data-* attributes on the link,<br>
which can be very useful when calling minLight on more than one link at a time.

e.g.

	<a href="something.jpg" title="alt text" data-fade-time="300" data-img-width="750"
		data-container="#main" data-target="#awesome-lightbox">Open Lightbox</a>

__Order of precendence: data-* attributes > options passed on creation > defaults__

	Lightbox.defaults = {
		fadeTime: "fast",
		easing: "swing",
		container: "body",
		// The actual lightbox the element should correspond to
		// If one already exists hidden on the page,
		// add its selector here
		target: "",
		maskClass: "",
		// Image href (usually assigned from the anchor's href)
		href: "",
		imgWidth: "auto",
		imgHeight: "auto",
		// Close the lightbox when the mask is clicked
		closeOnMaskClick: true,
		// Expand the mask to handle document height being larger than window height
		// This is sometimes not ideal if the container is something other than the body
		expandMask: true,
		// The basic skeleton for a lightbox
		// Don"t use a data-* attribute to set this (that's just ugly)
		skeleton: "" +
			"<div class='lightbox'>" +
				"<a href='#' class='lightbox-close ir'>X</a>" +
			"</div>"
		// onOpen, onClose cannot be extended with data-*, so they are included in defaults
		// they can be passed on creation or changed with the `option` method
	};

## Methods

Methods can be called in the same way as a widget from the UI widget factory. Pass a method name to minLight. Strings are interpreted as method names.

### `open`

	$link.minLight("open");

Open the lightbox

### `close`

	$link.minLight("close");

Close the lightbox

### `destroy`

	$link.minLight("destroy");

Unbinds all events and removes all data, including the minLight instance on the element.

### `instance`

	var minInstance = $link.minLight("instance");

Retreives the minLight instance(s) from the set. If there are multiple, you will get an array of instances. If there is only one, you will just get the instance of minLight.

### `option`

	// One at a time
	$link.minLight("option", "onOpen", function() {
		// Replace the onOpen callback
	});

	// Several options at once
	$link.minLight("option", {
		fadeTime: "fast",
		container: "#main",
		maskClass: "super-mask"
	});

Any option can be changed. See the defaults above for a list.
