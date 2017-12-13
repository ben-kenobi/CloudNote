#OpenGLES 2.0
> to use 2.0,glSurfaceView.setEGLContextClientVersion(2);

### 使用步骤
1. create a subclass of GLSurfaceView,and set it as Activity's contentView
2. in glSur,handle touchEvent,and set a renderer to it in constructor and set renderMode;
3. **renderer's onSurfaceViewCreated method:** set clear color and other functions,new a shape,and init texture
4. in shape,initVertexData and init Shaders from vertex.sh and frag.sh file,obtain the handles of attribute and uniform and the program
5. **renderer's onSurChanged method:** set the Viewport, and setup projFrustum and camera,init curMatrix
6. **renderer's onDrawFrame method:** clear buffer and draw the shape
7. **in shape's draw method:** set use Program,setup curMatrix,and set the MVPMatrixHandle's value,set values to attributes's handle with ByteBUffer or FloatBuffer,set values to uniform's handle as well,enable attribute's handle,activeTexture and drawArrays with the renderer flow

