# DevizPRO V49 — Sistem vizual / Visual system

## Română

V49 introduce un cadru vizual comun pentru toate modulele existente, fără a înlocui funcțiile sau modelul de date. Antetul folosește marca DevizPRO, navigarea este o bară laterală pe desktop și o bandă orizontală derulabilă pe ecrane mici. Toate paginile folosesc aceeași paletă verde-pădure/mentă, suprafețe albe, margini fine, umbre discrete, câmpuri coerente și stări de focalizare vizibile.

Principii: densitate utilă fără aglomerare; ierarhie tipografică; ținte tactile de minimum 40 px; navigare directă către toate modulele; layout adaptiv; respectarea `prefers-reduced-motion`; fără fonturi, imagini sau biblioteci externe obligatorii.

Marca raster generată este disponibilă în `Logo/`; simbolul SVG vectorial este `Logo/devizpro-mark.svg`. Pictogramele PWA 192/512 sunt regenerabile din sursa transparentă.

## English

V49 introduces a shared visual shell for all existing modules without replacing their features or data model. The header uses DevizPRO branding; navigation is a desktop side rail and a horizontally scrollable strip on small screens. All pages share the same forest-green/mint palette, white surfaces, subtle borders and shadows, consistent form controls, and visible focus states.

Principles: useful density without clutter; clear typographic hierarchy; touch targets of at least 40 px; direct navigation to every module; responsive layout; respect for `prefers-reduced-motion`; no mandatory external fonts, images, or libraries.

The generated raster mark is available in `Logo/`; the scalable vector mark is `Logo/devizpro-mark.svg`. PWA icons at 192/512 px can be regenerated from the transparent source.

## Extensii V49 / V49 extensions

RO: Pagina principală are patru carduri cu imagini și acțiuni rapide. Cardurile de obiect din Măsurători folosesc miniaturi WebP locale; dimensiunile sunt într-un rând compact, acțiunile sunt separate, iar clipping-ul este afișat în interiorul părintelui. Viewerul foto este fullscreen; editorul folosește canvas, toolbar superior, unelte verticale și salvare ca o copie separată.

EN: The home page has four image-based quick actions. Measurements object cards use local WebP thumbnails; dimensions are compact, actions are separated, and clipping is shown inside its parent. The photo viewer is fullscreen; the editor uses canvas, a top toolbar, vertical tools, and save-as-copy behavior.
