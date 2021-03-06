.. meta::
   :github: https://github.com/bimdata/documentation/blob/dev/doc_sphinx/viewer/parameters.rst

=========================
Parameters and methods
=========================

You can change the display of the Viewer using the value of attributes, and using the methods.

Attributes
============

List of attributes of the ``BIMDataViewer``:

*	``.helper``: instance of *ViewerHelper* (Type: *object*)
*	``.iframe``: the *HTMLElement* <iframe>
*	``.elementHovered``: name of the element (Type: *string*), read-only
*	``.elementsHovered``: list of names of the elements, read-only
*	``.elementHighlighted``: name of the element (Type: *string*)
*	``.elementSelected``: name of the element (Type: *string*)
*	``.elementsHighlighted``: list of names of the elements (Type: *array*)
*	``.elementsSelected``: list of names of the elements (Type: *array*)
*	``.elementsHided``: list of names of the elements (Type: *array*)
*	``.elementsGhosted``: list of names of the elements (Type: *array*)
*	``.buttonsMenuActivated``: { [ buttonId ]: *boolean* isActivated?  } (Type: *Object*), read-only
*	``.buttonsMenuShowed``: { [ buttonId ]: *boolean* isVisible } (Type: *Object*), read-only

Methods
==========

The interface BIMDataViewerInterface let you have actions on the Viewer via many methods.

Delete
--------


.. js:method:: BIMDataViewer.drop()

    Delete the Viewer

    :returns: void

Window
-------

Methods to interact with custom windows of the Viewer

.. js:method:: BIMDataViewer.addCustomWindow(id, options)

    Creation of a custom window, initialization with the parameters given in the ``options`` Object

    :param string id: ID of the Window
    :param object options: Instance of BIMViewerParamsCustomWindowOptions
    :returns: void

    .. code-block:: javascript

                    viewer1.addCustomWindow('first-window', {
                        open: true,
                        template: 'awesome'
                    })


.. js:method:: BIMDataViewer.addCustomButtonMenu(id, options)

    Attach a button to the Options menu

    :param string id: ID of the Menu,
    :param object options: *Object* BIMViewerCustomButtonOptionsMenu
    :returns: void


.. js:method:: BIMDataViewer.removeCustomWindow(id)

    Delete the previously created custom window

    :param string id: ID of the custom Window
    :returns: void


.. js:method:: BIMDataViewer.openCustomWindow(id)

    Display the custom window previously created

    :param string id: ID of the custom Window
    :returns: void


.. js:method:: BIMDataViewer.closeCustomWindow(id)

    Close the custom window previously created


    :param string id: ID of the custom Window
    :returns: void


.. js:method:: BIMDataViewer.setCustomWindowTemplate(id, template)

    Apply a template to the custom window

    :param string id: ID of the custom Window
    :param string template: name of the template
    :returns: void


.. js:method:: BIMDataViewer.onCustomWindow(idWindow, event, selector, callback, preventDefault)

    Associate a behavior, via a function, to the custom window event(s)

    :param integer idWindow: ID of the custom Window
    :param string event: name of the event
    :param string selector: CSS-style selector
    :param function callback:
    :param boolean preventDefault:

    :returns: integer windowNumber: auto-increment numeration of the custom Windows


.. js:method:: BIMDataViewer.offCustomWindow()

    Event of the disparition of a custom window

    :param string id: ID of the custom Window
    :returns: void


Buttons
----------

Methods to interact with the buttons of the Viewer's menus.
All these methods return *void*.


.. js:method:: BIMDataViewer.activateButtonMenu(target, visibility)

    Activate a button of the menu 

    :param string target: name of the button
    :param boolean visibility:
    :returns: void


.. js:method:: BIMDataViewer.showButtonMenu(target, visibility)

    Display a button 

    :param string target: name of the button
    :param boolean visibility:
    :returns: void


.. js:method:: BIMDataViewer.showSelectModeMenu(target, visibility)

    :param string target:name of the button
    :param boolean visibility:
    :returns: void


.. js:method:: BIMDataViewer.addCustomButtonMenu(id, options)

    :param integer id: ID of the menu
    :param object options: *Object* instance of ``BIMViewerCustomButtonOptionsMenu``
    :returns: void


.. js:method:: BIMDataViewer.removeCustomButtonMenu(id)

    :param integer id: ID of the menu
    :returns: void


Reach the Viewer
-----------------

More generic methods to reach the Viewer and set it.

.. js:method:: BIMDataViewer.on(eventName, callback)

    Associate a behavior, through a function, to the Viewer event(s)

    :param string eventName: name of the targeted event
    :param function callback: *Function* [callback]
    :returns: number: an auto-increment ID for this Viewer instance


.. js:method:: BIMDataViewer.off(id)

    :param integer id: ID of the Viewer
    :returns: void


Elements & IFC
----------------

Methods to interact with elements of your Model.

.. js:method:: BIMDataViewer.setPickable(selector)

    Set an element of the model as pickable for selection

    :param string selector: CSS-style selector
    :returns: void


.. js:method:: BIMDataViewer.setUnpickable(selector)

    Set an element of the model as non-pickable for selection

    :param string selector: CSS-style selector
    :returns: void


.. js:method:: BIMDataViewer.getElementsInfo(ifcId)

    Get an element/collection of elements of your model and their information

    :param integer ifcId:
    :returns: objects { [id: string]: any }


.. js:method:: BIMDataViewer.getModel(uuid)

    Get the Model object

    :param integer uuid:
    :returns: model


.. js:method:: BIMDataViewer.getStructure(uuid)

    Get the structure of the Model

    :param integer uuid:
    :returns:  Promise *Function*


Interface
---------

Methods to modify the display, the view, and point of view.

.. js:method:: BIMDataViewer.getColor(id)

    :param integer id: ID of the IFCElement
    :returns: color: Promise<[ *number*, *number*, *number* ]


.. js:method:: BIMDataViewer.setColor(selector, color)

    :param string selector:
    :param array color:  [ *number*, *number*, *number* ]
    :returns: void


.. js:method:: BIMDataViewer.getSnapshot(options)

    Captures a snapshot image of the viewer's canvas.

    :param object options: { *integer* width, *integer* height, *string* format: *"png|jpeg|bmp"* }
    :param integer width: Desired width of result in pixels - defaults to width of canvas.
    :param integer height: Desired height of result in pixels - defaults to height of canvas.
    :param string format: Desired format; "jpeg", "png" or "bmp", default is *"jpeg"*
    :returns: *string* String-encoded image data

   .. code-block:: javascript

        imageElement.src = viewer.getSnapshot({
            width: 500,
            height: 500,
            format: "png"
        });


.. js:method:: BIMDataViewer.getViewpoint()

    :returns: *Object* instance of <ViewPoint>


.. js:method:: BIMDataViewer.setViewPoint(viewpoint)

    :param object viewpoint: instance of <ViewPoint>
    :returns: void


.. js:method:: BIMDataViewer.viewFit()

    Put the focus on the given element(s)

    :param string selector: CSS-style selector
    :returns: void


.. js:method:: BIMDataViewer.select()

    :param string selector: CSS-style selector
    :returns: void


.. js:method:: BIMDataViewer.deselect()

    :param string selector: CSS-style selector
    :returns: void


.. js:method:: BIMDataViewer.highlight()

    put the element(s) in the highlight color

    :param string selector: CSS-style selector
    :returns: void


.. js:method:: BIMDataViewer.dehighlight()

    remove the highlight from the element(s)

    :param string selector: CSS-style selector
    :returns: void


.. js:method:: BIMDataViewer.show()

    :param string selector: CSS-style selector
    :returns: void


.. js:method:: BIMDataViewer.hide()

    :param string selector: CSS-style selector
    :returns: void


.. js:method:: BIMDataViewer.unghost()

    no more transparency for the given element(s)

    :param string selector: CSS-style selector
    :returns: void


.. js:method:: BIMDataViewer.ghost()

    set transparency to the maximum for the given element(s)

    :param string selector: CSS-style selector
    :returns: void
