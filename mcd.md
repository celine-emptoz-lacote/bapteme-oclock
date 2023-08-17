
Les noms de tes entitiés sont bons et en anglais , ainsi que le nom de tes champs, c'est bien.

Les rélations entre les tables ne peuvent etre représentées par des rectangles.

Dans ta table USER, il te manque des informations personnelles comme le nom , le prénom.

Je pense que certaines de tes cardinalitées sont fausses :

 - La relation entre la table address et user. Un user peut il vraiment avoir zéro adresse de livraison ? Dans les consignes c'est indiqué que l'acheteur peut avoir 1 ou plusieurs adresses.  Donc la relation entre USER et ADDRESS serait de 1/N au minimum 1 et au max plusieurs.
 - La relation entre la table USER et PRODUCT. Si tu as de chaque coté une relation de type 1/1 cela ne peut etre une relation de type many-to-many. D'ailleurs, un user est il obligé d'aime au minimum 1 produit et maximum 1 ? Non. Il peut en aimer zero ou plein. Donc la relation serait donc plutot USER ==> PRODUCT de type 0/N et de PRODUCT  ==> USER de type 0/N. Effectivement un produit peut etre aimer par personne ou par beaucoup de personnes.