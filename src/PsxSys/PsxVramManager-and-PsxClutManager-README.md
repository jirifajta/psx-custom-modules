# PSX Modules

**PsxVramManager** & **PsxClutManager** are modules for PSX to make _textures_ and _cluts_ (color lookup tabels) handling in VRAM easier.
Default way of doing this, is to locate textures and cluts is to code offset in PSX _Tim_ (alike) files.

This default method has some drawbacks:
1. Planning entire VRAM mapping where textures and cluts needs to be placed.
2. Texture will be always placed at same location.
3. Clut will be always placed at same location and it can potentially stay in a way to place a texture.
4. These make texture streaming less flexible (i.e. texture swapping).

PsxVramManager & PsxClutManager do not care about coded coordinates in Tim files where to locate them in VRAM, rather it checks available empty location in VRAM managed by PsxVramManager & PsxClutManager. It returns pointer where texture and clut where placed in VRAM such that it can be applied to primitives.

Therefore no need to worry where textures and cluts will be placed in VRAM. This makes textures and cluts streaming easy.


**REQUIRMENT:**
Insert all your frame buffers as texture into VramManager/VramCollection such that inserted textures will not be overlayed on frame buffers.
Use function _vram_manager_insert_particular_area(...)_ to set these buffers.
If using PsxClutManager which is optional, then also insert this one to allocate space in VRAM (default size is 256x64 pixels).

**LIMITATION:**
Max texture height supported is 256 pixel data in VRAM. This is due to tpage limitation. 

**NOTE:**
By default _cell_in_pixels_size_ is set to 32x32 pixel data in VRAM which divides VRAM into 32x32 pixel blocks.
This size opens the possiblity that textures of less then multiple of 64x256 pixel data size can be  tpage unaligned in VRAM. This means that texture does not start at tpage coordinate and because of offset, textures will be wrong mapped to primitives if texture coords (UV) are not changed accordingly.
There are two options how to handle this:
1. Use always textures of multiple of 64x256 pixel data size. Like 64x256, 128x256, 256x256, 320x256, and so on.
2. Or, after inserting texture, use _vram_manager_vram_align_delta(...)_ function to adjust the offset of texture coords. This function calculates the offset.
   And use _vram_manager_move_vt_based_on_not_aligned_texture_update_vt_only(DVECTOR *vt_shift, DVECTOR *vts, u_long num_vt)_ to apply the offset to the primitives UV.
