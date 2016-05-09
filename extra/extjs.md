1. ExtJS introduction
    1. smartclient, kendo ui
    1. Real examples
        1. [synology](https://www.synology.com/en-us/dsm/5.2/live_demo)
        1. [sitescout](https://rtb.sitescout.com/)
    1. History
        1. 3.x (2009.07)
            1. stable & fast
        1. 4.x (2011.04)
            1. Not compatible with 3.x
            1. Class system & Ext.define
            1. Sencha MVC
            1. Rewritten dom infrastructure, Ext.suspendLayouts/resumeLayouts
        1. 5.x (2014.06)
            1. MVVM, ViewController, ViewModel
            1. Routing
            1. Responsive
            1. More widgets, breadcrumb bar, tagfield, spreadsheet(5.1), color picker(5.1), rating widget(5.1)
            1. Components in grid cells
            1. No support for IE6 & 7
            1. Mobile(tablet) support
            1. Sencha command
        1. 6.x (2015.04)
            1. Merging Extjs and Touch
            1. Promise
            1. microloader, localstorage
            
	1. Examples:
		1. Forms, ComboBox, Grids, Windows, Layout Managers, Toolbars and Menus
		1. DataView
		1. Tabs, Trees
		1. Drag & Drop

1. ExtJS development
	1. Class system
    1. [http://www.extjs-tutorial.com/extjs/naming-convention](http://www.extjs-tutorial.com/extjs/naming-convention)
    1. UI components
        1. Element & Container
        1. Layouts
    1. Layout system
        1. absolute, table
        1. fit, border, accordion, card
        1. auto, anchor, form, vbox
        1. hbox, column
    1. Store, Model, Proxy, View
    1. Events

1. ExtJS Doc
    1. Ext.Component
        1. config
            1. id, itemId
            1. margin, padding
            1. width, height, minWidth, minHeight, maxWidth, maxHeight
            1. autoScroll
            1. cls, style, baseCls
            1. border, frame
            1. hidden, hideMode
            1. disabled, disabledCls
            1. autoEl
            1. tpl
            1. stateful, stateId
        1. method
            1. disable(), enable()
        1. custom component
            1. [http://docs.sencha.com/extjs/4.2.1/#!/guide/components-section-creating-custom-components](http://docs.sencha.com/extjs/4.2.1/#!/guide/components-section-creating-custom-components)
    1. Form fields
        1. config
            1. name
            1. fieldLabel, fieldStyle, fieldCls
            1. labelWidth, labelAlign, labelCls, labelStyle, labelSeparator
            1. hideEmptyLabel, hideLabel
            1. readOnly, readOnlyCls, disabled, disabledCls, emptyCls, emptyText, dirtyCls
            1. originalValue, isDirty(), dirtyCls
            1. enforceMaxLength
            1. enableKeyEvents
            1. submitValue
            1. formBind
            1. Validation text & class
                1. vtype
                1. validator
                1. allowBlank
                1. msgTarget
                1. blankText, invalidText, invalidCls
        1. methods
            1. getValue(), getRawValue()
            1. getActiveErrors(), setActiveErrors(), getErrors(), markInvalid()
            1. isValid(), clearInvalid()
            1. checkChange(), checkDirty(), isDirty(), resetOriginalValue()
            1. rawToValue(), valueToRaw()
    1. Containers: container, panel, window, form, tab, fieldset, fieldcontainer
        1. config
            1. bubbleEvents
            1. defaults, defaultType
            1. items
            1. layout
        1. method
            1. add(), remove(), removeAll
            1. child(), down()
    1. Form
        1. method
            1. getValues()
            1. isDirty(), isValid()
            1. load(), submit(), loadRecord(), getRecord()
            1. getForm()
        1. Basic
            1. getFieldValues(), getValues()
            1. findField(), getFields()
            1. isDirty(), isValid()
            1. checkDirty(), checkValidity(), clearInvalid(), markInvalid()
            1. load(), submit(), loadRecord(), getRecord(), setValues()
    1. Data Package
        1. Ext.data.Store
            1. fields: name, type
            1. model
            1. each(), getAt()
            1. getCount(), getTotalCount()
        1. Ext.data.Model
            1. fields, idProperty
            1. get()
            1. isModified()
            1. commit(), reject()
            1. validations
            1. validate(), isValid(), dirty
        1. Ext.data.proxy.Proxy
            1. url
            1. api
            1. timeout: global setting
            1. extraParams
            1. limitParam, pageParam etc.
            1. reader
        1. Ext.data.reader.Json
            1. successProperty, totalProperty, root
        1. Sample
            ```javascript
            me.store = new Ext.data.Store({
                proxy: {
                    type: 'ajax',
                    url: 'path/getUserAccountBalances',
                    extraParams: {
                        userId: me.getUserId()
                    },
                    reader: {
                        type: 'json',
                        root: 'items'
                    }
                },
                fields: [
                    {name: 'CURRENCY'},
                    {name: 'CURRENCYBALANCE', type : 'float'},
                    {name: 'DEFAULT', type: 'boolean'}
                ],
                listeners: {
                    load: function(s, records, success) {
                        
                    }
                }
            });
            ```
    
    1. Grid
        1. column
            1. text, dataIndex, renderer
        1. viewConfig
            1. trackOver, enableTextSelection, markDirty, stripeRows
    1. ComboBox
        1. store
        1. listConfig
            1. width, height, minWidth, maxWidth, minHeight, maxHeight
            1. itemSelector, getInnerTpl
    1. View
    1. Tree/Time
    1. Events
        1. listeners : { }
        1. addListener(), on()
        1. addManagedListener(), mon()
        1. removeListener(), removeManagedListener(), un(), mun()
        1. fireEvent(), fireEventArgs()
    1. Component Query
        1. CSS selector
            1. [http://www.w3schools.com/cssref/css_selectors.asp](http://www.w3schools.com/cssref/css_selectors.asp)
            1. [https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Getting_started/Selectors](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Getting_started/Selectors)
            1. [http://code.tutsplus.com/tutorials/the-30-css-selectors-you-must-memorize--net-16048](http://code.tutsplus.com/tutorials/the-30-css-selectors-you-must-memorize--net-16048)
        1. method
            1. container: down(), child(), query()
            1. Component: up(), nextSibling(), nextNode(), previousSibling(), previousNode()
        1. syntax
            1. itemId: #
            1. xtype: xtype
            1. property: xtype[property=""]
            1. [http://docs.sencha.com/extjs/4.2.0/#!/api/Ext.ComponentQuery](http://docs.sencha.com/extjs/4.2.0/#!/api/Ext.ComponentQuery)
        1. performance
            1. do not use it in a loop
            1. cache the result
1. resources
    1. [http://www.sencha.com/blog/top-10-ext-js-development-practices-to-avoid/](http://www.sencha.com/blog/top-10-ext-js-development-practices-to-avoid/)

1. SenchaMVC
	1. application

        ```javascript
        Ext.application({
            name: 'Homework',
            appFolder: 'app',
            requires: [
                ...
            ],

            launch: function() {
                Ext.create('Ext.container.Viewport', {
                    layout: 'fit',
                    items: [{
                        ...
                    }]
                });
            }
        });
        ```

		vs

        ```javascript
        Ext.Loader.setPath('Homework', 'app');

        Ext.require([
            ...
        ]);

        Ext.onReady(function() {
            Ext.create('Ext.container.Viewport', {
                layout: 'fit',
                items: [{
                    ...
                }]
            });
        });
        ```

	1. controller
		1. refs
		1. models, views, stores
		1. init(), control()

1. Advanced ExtJS
	1. Form validation
	1. Tree
	1. View
	1. Custom control
	1. DOM

1. ExtJS dev rules
    1. no id
    1. no global functions
    1. no functions in strings

1. ExtJS interview questions
    1. [http://www.withoutbook.com/Technology.php?tech=65&subject=ExtJS%20Interview%20Questions%20and%20Answers](http://www.withoutbook.com/Technology.php?tech=65&subject=ExtJS%20Interview%20Questions%20and%20Answers)
    1. [http://atoz-tech.blogspot.ca/2011/07/extjs-interview-questions.html](http://atoz-tech.blogspot.ca/2011/07/extjs-interview-questions.html)
    1. [http://interviewquestionsanswers.org/forum/topic-1553-65-ext-js-interview-questions-and-answers-page-1.html](http://interviewquestionsanswers.org/forum/topic-1553-65-ext-js-interview-questions-and-answers-page-1.html)
    1. [http://www.globalguideline.com/interview_questions/Questions.php?sc=Ext_JS](http://www.globalguideline.com/interview_questions/Questions.php?sc=Ext_JS)
    1. [http://sureshat25.blogspot.ca/2014/12/ext-js-interview-question-and-answers.html](http://sureshat25.blogspot.ca/2014/12/ext-js-interview-question-and-answers.html)
    1. [http://extjsexamples.blogspot.ca/2013/05/extjs4-interview-questions-answers.html](http://extjsexamples.blogspot.ca/2013/05/extjs4-interview-questions-answers.html)
