<style src="./annotationLayer.css"></style>
<script>

	import componentFactory from './componentFactory.js'

	if ( process.env.VUE_ENV === 'server' ) {

		var component = componentFactory({});
	} else {

		var pdfjsWrapper = require('./pdfjsWrapper.js').default;
		// use other webpack init script - allow worker-loader overrides
		var PDFJS = require('pdfjs-dist/webpackNoExplicitLoader.js');
		var component = componentFactory(pdfjsWrapper(PDFJS));
	}

	export default component;
</script>
