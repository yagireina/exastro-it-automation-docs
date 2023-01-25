======================================
Exastro IT Automation Organization API
======================================

.. raw:: html

   <div id="swagger-ui"></div>

   <script>
   $(function(){

     $('h1').remove();
     $('#article').attr('id', 'swaggerBody');

     $api_urls = [
       {url: "https://raw.githubusercontent.com/exastro-suite/exastro-it-automation/2.0/ita_root/ita_api_organization/swagger/swagger.yaml", name: "v2.0"}
     ]

     // Begin Swagger UI call region
     const ui = SwaggerUIBundle({
       urls: $api_urls,
       dom_id: '#swagger-ui',
       deepLinking: true,
       presets: [
         SwaggerUIBundle.presets.apis,
         SwaggerUIStandalonePreset
       ],
       plugins: [
         SwaggerUIBundle.plugins.DownloadUrl
       ],
       layout: "StandaloneLayout",
     });
     // End Swagger UI call region

     window.ui = ui;
   });
   </script>