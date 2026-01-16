1. În lumea reală, lumina urmează legi fizice (propagare continuă, reflexii multiple, refracție, împrăștiere, absorbție, umbre corecte etc.), iar rezultatul depinde de materiale și de mediul prin care trece lumina.
​
În OpenGL fixed‑function (stilul „vechi”, folosit des în exemple OpenTK), iluminarea e un model local simplificat (tip Phong/Blinn‑Phong clasic: ambient + difuz + specular), calculat de obicei per‑vertex (Gouraud shading) și fără umbre „reale” sau reflexii globale.
​

2. În pipeline‑ul fixed‑function, OpenGL are suport pentru 8 surse de lumină, numerotate GL_LIGHT0 până la GL_LIGHT7 (asta e limita clasică, valabilă și când folosești OpenTK cu acest mod).
​

3. Iluminarea de material reprezintă „cum reacționează suprafața obiectului la lumină”: componente ca ambient/difuz/specular (și uneori emissive) plus „shininess” (cât de concentrat e highlight‑ul specular).
​
Este utilizată atunci când randarea se face cu GL_LIGHTING activ și se setează proprietățile materialului (ex. prin glMaterial* / echivalent), înainte de desenarea geometriei, ca OpenGL să poată calcula culoarea finală sub iluminare.
​

4. Când activezi o a doua sursă de lumină, contribuțiile ei (ambient/difuz/specular) se adaugă la iluminarea deja existentă, deci obiectele pot deveni mai bine luminate din mai multe direcții și apar highlight‑uri suplimentare sau zone întunecate „mai puțin plate”.
​
Cu o singură sursă, scenele arată mai „unidirecțional” (contrast puternic pe o parte și întunecare pe cealaltă), iar cu două surse poți obține o iluminare mai echilibrată (mai ales dacă a doua lumină e mai slabă, ca un „fill light”).
​