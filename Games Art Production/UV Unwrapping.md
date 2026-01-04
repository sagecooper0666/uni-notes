UV mapping changes based on the asset itself, characters, props etc. UV mapping is the foundational process that allows 2D textures to wrap correctly into 3D assets. The UV tetuxures correspond to the amount of polygons within a model as well as vise versa. Can be seen as unfurling a cardboard box into a flat pattern. The U and V coordinates represent the horizonal and vertical axes. Every point on the 3D surface must correspond to a specific location on the flat texture. The quality will diretly impart the texture resolution, seam visibility, baking accurecy, etc.

**Identifying quality UV layouts**

| Good UV                                                    |     | Poor UV                                     |
| ---------------------------------------------------------- | --- | ------------------------------------------- |
| Even, uniform checkerboard pattern across surface          |     | Stretched or squashed checkerboard patterns |
| Minimal stretching or distortion                           |     | Rnadom seam placement on visible surface    |
| Cleanly placed seams, hidden or logically positioned       |     | Unintentional overlapping of uv islands     |
| Organised, non-overlapping UV islands (unless intentional) |     | Inconsistant texel density between areas    |
| Efficient packing that maximises texture space uses        |     | wasted empty space in the UV layout         |
| Consistant texel density across the entire model           |     | jagged, twisted or poorly shaped islands    |
|                                                            |     |                                             |
|                                                            |     |                                             |
**Stylised Game UV Approaches**
Stylised art prioritise flow and readability over photorealistic precision. *fewer seams* allow hand painted texture strokes to flow naturally across the surface without interruption.
- Mild stretching is acceptable and often unnoticeable 
- UV mirroring is common for *symmetrical* characters
- focus on simplicity 
- lower texture realism means UV precision is less critical
- Artistic expression takes priority over technical perfection
**Realistic game UV Approaches**
Realistic games require more detail within the UV layout and as little distortion as physically possible for the best results. This also includes precise seam placements for normal map baking. no mirroring on unique detail areas, high texel density, and technical precision. 

**Understanding UV channel 0: Albedo and Texture UV**
the primary UV channel (channel 0) handles all visual texture detail that defines how your asset appears in the game world. These UVs are what the artist ineracts with the most frequently during the texturing process. 

| Texture Types Using UV channel 0                      |     |
| ----------------------------------------------------- | --- |
| Base Colour (albedo) - the fundemental surface colour |     |
| Normal Map - surface detail and micro-gemonetry       |     |
| Roughness/metalness - material properties for PBR     |     |
| emissive - Self-illuminating areas                    |     |
| Ambient Occlusion - Contact shadows (sometimes)       |     |
|                                                       |     |

| Critical Rule For Texture UVs                                      |     |
| ------------------------------------------------------------------ | --- |
| Overlaps allowed - symmetry and repeating parts can share UV space |     |
| Minimal stretching - maintain consistant textel density            |     |
| Clean seam placement - Hide seams or place them logically          |     |
| Consistant density - ensure unirom detail across surface           |     |
These UVs focus entirely on *visual quality*. Every decision about layout, seam placement, and island organisation serves the goal of creating beautiful, high quality textures that look correct from all viewing angles in-game.

**Understanding UV channel 1: Lightmap UVs**
lightmaps UVs serve as an entirely different purpose from texture UVs. These specialised UV layouts are used by game engines like unreal Engine to bake static lighting information creating pre-calculated shadows and light bounces that enhance visual quality whilst maintaining performance.


| ABSOLUTE REQUREMENTS                                           | Acceptable Compromises                         |
| -------------------------------------------------------------- | ---------------------------------------------- |
| *NO OVERLAPS WHATSOEVER* - every surface needs unique UV space | Island orientation doesn't matter for lighting |
| All islands must fit completely within 0-1 unique UV space     | More seams are perfectly acceptable            |
| Strong padding between islands to prevent light bleeding       | Stretching                                     |
[^1]

[^1]: crititcal Distinction: Whilst texture UVs prioritise visial painting and detail, lightmap UVs focus exlusevly on clean, artefact-free lighting calculations. Never use overlapping UVs in your lightmap, channel as this causes severe

**Strategic seam placement for characters**
character models present unique UV challenges becuase they defor m during animation and are frequently viewed at close range. Seam placement must be stratigic and methodical to prevent visible texture breaks during movement. 

| Optimal Seam Locations                                                                                |                                                                                          |
| ----------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Characters require carefully hidden seams that remain concealed during typical gameplay and animation | Never Place seams in locations that compromise visual or become obvious during animation |
| inner arms - naturally hidden during most poses                                                       | Facial fetures - alwatys highly visible                                                  |
| inner legs - typically not visible to camera                                                          | knees and elbows - deform extensively                                                    |
| centre of back - covered by hair or clothing                                                          | shoulder tops - constant camera visibility                                               |
| clothing edges - natural material transitions                                                         | curved, visible surfaces - seams become apparent                                         |
| inside ears - shadowed and rerely visible                                                             | animation contact points - texture misalignment shows                                    |
| mouth interior - only visible during speech                                                           |                                                                                          |
|                                                                                                       |                                                                                          |
Remember that characters undergo complex skeletal deformation. Seams placed on deforming areas can separate visibly during animation, breaking immersion and revealing technical limitations.

**Seam Strategy for Props and Hard-surface Models**
Hard surface props and objects offer a lot more flexibility with UV seams than organic characters. Because props remain static or undergo simple transformations without skeletal deformation, seam placement becomes more forgiving whilst still requiring thoughtfu planning.

Utilise hard edges - place seams along 90-degree angles and sharp corners where they naturally disappear into the geometry edge definition. 
Leaverage hidden surfaes - position seams on undersides. back faces or areas typically not visible during normal gameplay viewing angles.
Follow material Transitions - align seams with changes in material type, such as where metal meets plastic or wood joins metal components.
Respect corner Geometry- corners and edfe intersections provide seam locations 

tileable textures 
modular requirements 
lightmap priority 
trim sheet systems 
hero assets 
exceptions 
seams tolerance 
