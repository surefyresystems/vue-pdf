<style src="./annotationLayer.css"></style>
<script>

	import componentFactory from './componentFactory.js'
	import PDFJS from 'pdfjs-dist/build/pdf.js';

	if ( process.env.VUE_ENV !== 'server' ) {

		var pdfjsWrapper = require('./pdfjsWrapper.js').default;

		if ( typeof window !== 'undefined' && 'Worker' in window && navigator.appVersion.indexOf('MSIE 10') === -1 ) {
			PDFJS.GlobalWorkerOptions.workerSrc = gSurefyreStaticUrl + "pdfjs/pdf.worker.min.js";
		}

		var component = componentFactory(pdfjsWrapper(PDFJS));
	} else {

		var component = componentFactory({});
	}

	export default component;
</script>
