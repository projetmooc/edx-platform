
.. _Appendix E:


^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
APPENDIX E: Problem and Tool XML
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This appendix provides information about the XML tags for most problem and tool types in Studio:

* :ref:`General`
* :ref:`Choice Response`
* :ref:`Chemical Equation Input`
* :ref:`Custom Response`
* :ref:`Drag and Drop XML`
* :ref:`Formula Response`
* :ref:`Image Response`
* :ref:`Multiple Choice Response`
* :ref:`Numerical Response`
* :ref:`Option Response`
* :ref:`Schematic Response`
* :ref:`String Response`


.. _General:

=======
General
=======
 
Most problems have the following tags.

.. list-table::
   :widths: 20 80

   * - ``<problem> </problem>``
     - These must be the first and last tags for any content created in the Advanced
       Editor in a Problem component.
   * - ``<startouttext/>``
     - The ``<startouttext />`` tag indicates the beginning of a line or block of text.
   * - ``<endouttext/>``
     - The ``<endouttext />`` tag indicates the end of a line or block of text.
   * - ``<solution> <div class="detailed-solution"> </div> </solution>`` (optional)
     - If you want to include more information in the problem, such as a detailed explanation of the problem's answer, you'll enter the text between the two ``<div>`` tags, which are inside the ``<solution>`` tags. (These tags do not have to be on the same line.)

Additionally, all problems must include a **label** attribute. This attribute adds a descriptive label that helps visually impaired students navigate through the problem.

You'll add a **label** attribute to one of the XML tags for the problem. Each example problem below includes a label.

.. _Checkbox Problem XML:

=============================
Checkbox Problem XML 
=============================

Template
--------

.. code-block:: xml

  <problem>
  <startouttext/>
    <p>Question text</p>

  <choiceresponse>

  <checkboxgroup direction="vertical" label="label text">
  <choice correct="false"><text>Answer option 1 (incorrect)</text></choice>
  <choice correct="true"><text>Answer option 2 (correct)</text></choice>
  </checkboxgroup>

   <solution>
   <div class="detailed-solution">
   <p>Solution or Explanation Heading</p>
   <p>Solution or explanation text</p>
   </div>
   </solution>

  </choiceresponse>
  </problem>

Tags
----

* ``<choiceresponse>`` (required): Specifies that the problem contains options for students to choose from.
* ``<checkboxgroup>`` (required): Specifies that the problem is a checkbox problem.
* ``<choice>`` (required): Designates an answer option.

**Tag:** ``<choiceresponse>``

  Children

  .. list-table::
     :widths: 20 80

     * - Children
       - Description
     * - ``<checkboxgroup>``
       - Specifies that the problem is a checkbox problem. 


**Tag:** ``<checkboxgroup>``

  Attributes

  .. list-table::
     :widths: 20 80

     * - Attribute
       - Description
     * - direction (optional)
       - Specifies the orientation of the list of answers. The default is vertical.
     * - label (required)
       - Specifies the name of the response field.

  Children

  .. list-table::
     :widths: 20 80

     * - Children
       - Description
     * - ``<choice>``
       - Designates an answer option. 

**Tag:** ``<choice>``

  Attributes

  .. list-table::
     :widths: 20 80

     * - Attribute
       - Description
     * - true (at least one required)
       - Indicates a correct answer. For checkbox problems, one or more ``<choice>`` tags can contain a correct answer.
     * - false (at least one required)
       - Indicates an incorrect answer.

==========================
Dropdown Problem XML
==========================

Template
--------

.. code-block:: xml

  <problem>
  <p>
    Problem text</p>
  <optionresponse>
    <optioninput options="('Option 1','Option 2','Option 3')" correct="Option 2" label="label text"/>
  </optionresponse>
    <solution>
      <div class="detailed-solution">
      <p>Explanation or Solution Header</p>
      <p>Explanation or solution text</p>
      </div>
    </solution>
  </problem>

.. code-block:: xml

  <problem>
   <p>Problem text</p>
    <optionresponse>
     options="('A','B')"
      correct="A"/>
      label="label text"
    </optionresponse>
   
    <solution>
      <div class="detailed-solution">
      <p>Explanation or Solution Header</p>
      <p>Explanation or solution text</p>
      </div>
    </solution>
  </problem>

Tags
----

* ``<optionresponse>`` (required)
* ``<optioninput>`` (required)

**Tag:** ``<optionresponse>``

Indicates that the problem is a dropdown problem.

  Children

  .. list-table::
     :widths: 20 80

     * - Children
       - Description
     * - ``<optioninput>``
       - Lists the answer options. 

**Tag:** ``<optioninput>``

Lists the answer options.

  Attributes

  .. list-table::
     :widths: 20 80

     * - Attribute
       - Description
     * - options (required)
       - Lists the answer options. The list of all answer options is surrounded by parentheses. Individual answer options are surrounded by single quotation marks (') and separated by commas (,).
     * - correct (required)
       - Indicates whether an answer is correct. Possible values are "true" and "false". Only one **correct** attribute can be set to "true".
     * - label (required)
       - Specifies the name of the response field.




.. _Multiple Choice Problem XML:

=============================
Multiple Choice Problem XML 
=============================

Template
--------

.. code-block:: xml

  <problem>
  <p>Question text</p>
  <multiplechoiceresponse>
    <choicegroup type="MultipleChoice" label="label text">
      <choice correct="false" name="a">Incorrect choice</choice>
      <choice correct="true" name="b">Correct choice</choice>
    </choicegroup>
  </multiplechoiceresponse>

  <solution>
    <div class="detailed-solution">
    <p>Explanation or solution header</p>
    <p>Explanation or solution text</p>
    </div>
  </solution>
  </problem>

Tags
----

* - ``<multiplechoiceresponse>`` (required): Indicates that the problem is a multiple choice problem.
* - ``<choicegroup>`` (required): Indicates the beginning of the list of options. Contains the ``label`` attribute.
* - ``<choice>`` (required): Lists an option. This tag includes the ``correct`` and ``name`` attributes.

**Tag:** ``<multiplechoiceresponse>``

  Children

  .. list-table::
     :widths: 20 80

     * - Child
       - Description
     * - ``<choicegroup>``
       - Indicates the beginning of the list of options.
     * - All standard HTML tags
       - Can be used to format text.


**Tag:** ``<choicegroup>``

  Attributes

  .. list-table::
     :widths: 20 80

     * - Attribute
       - Description
     * - label (required)
       - Specifies the name of the response field.
     * - type (required)
       - Must be set to "MultipleChoice".

  Children

  .. list-table::
     :widths: 20 80

     * - Children
       - Description
     * - ``<choice>``
       - Designates an answer option. 

**Tag:** ``<choice>``

  Attributes

  .. list-table::
     :widths: 20 80

     * - Attribute
       - Description
     * - correct (at least one required)
       - Indicates a correct or incorrect answer. When the attribute is set to "true", the choice is a correct answer. When the attribute is set to "false", the choice is an incorrect answer. Only one choice can be a correct answer.
     * - name
       - A unique name that the back end uses to refer to the choice.



.. _Numerical Response:

Numerical Response (Numerical Input Problems)
---------------------------------------------



**XML Attribute Information**


XML_Tags.rst

.. _chemicalequationinput:

``<chemicalequationinput>``
-----------------------------

Description

Indicates that the answer to this problem is a chemical equation. 

Used in
:ref:`Chemical Equation`

Parent
``<customresponse>``

Children
``<answer type=loncapa/python>``: Contains the Python script that grades the problem.

Attributes

``size`` (required): Specifies the size of the field where the student enters a response.

``label`` (required):


.. _Formula Response:

Formula Response (Math Expression Input Problems)
-------------------------------------------------

.. list-table::
   :widths: 20 80
   :header-rows: 1

   * - ``<formularesponse>``
     - 
   * - ``<formulaequationinput>``
     - This tag includes the ``size`` and ``label`` attributes.
   * - ``<script type="loncapa/python">``
     - 


**XML Attribute Information**

XML_Tags.rst


.. _customresponse:

``<customresponse>``
----------------------

.. list-table::
   :widths: 20 80

   * - ``<customresponse>``
     - Indicates that this problem has a custom response. 
   * - ``<script type="loncapa/python">``
     - Indicates that the problem contains a Python script.
   * - ``<customresponse cfn="test_add_to_ten">``
     - 
   * - ``<customresponse cfn="test_add" expect="20">``
     - 
   * - <textline size="10" correct_answer="3"/>
     - This tag includes the ``size``, ``correct_answer``, and ``label`` attributes. The ``correct_answer`` attribute is optional.



.. _Drag and Drop XML:

Drag and Drop XML
-----------------

For more information about how to create drag and drop problems, see `XML Format of Drag and Drop Input
<https://edx.readthedocs.org/en/latest/course_data_formats/drag_and_drop/drag_and_drop_input.html>`_.



.. _Image Response:

Image Response (Image Mapped Input Problems)
--------------------------------------------

**XML Tags**

.. list-table::
   :widths: 20 80

   * - ``<imageresponse>``
     - Indicates that the problem is an image mapped input problem.
   * - ``<imageinput>``
     - Specifies the image file and the region the student must click. This tag includes the ``src``, ``width``, ``height``, and ``rectangle`` attributes.

**XML Attribute Information**

See XML_Tags.rst


.. _Option Response:

Option Response (Dropdown Problems)
-----------------------------------

**XML Tags**

.. list-table::
   :widths: 20 80

   * - ``<optionresponse>``
     - Indicates that the problem is a dropdown problem.
   * - ``<optioninput>``
     - Lists the answer options. This tag includes the ``options``, ``correct``, and ``label`` attributes.

**XML Attribute Information**

XML_Tags.rst

.. _problem:

``<problem> </problem>``
--------------------------

These must be the first and last tags for any content created in the Advanced Editor in a Problem component.

Used in: All

Parent: None

Children: Multiple

Attributes: None


.. _Schematic Response:

Schematic Response (Circuit Schematic Problems)
-----------------------------------------------

The Schematic Response input type provides an interactive grid on which the
student can construct a schematic answer, such as a circuit.

**Sample Problem**

.. image:: ../Images/CircuitSchematicExample.gif
 :alt: Image of a schematic response explanation



.. _stringresponse:

``<stringresponse>``
--------------------

.. list-table::
   :widths: 20 80

   * - ``<stringresponse>``
     - Indicates that the problem is a text input problem. 
   * - ``<textline>``
     - Child of ``<stringresponse>``. Lists the answer options and contains the ``label`` attribute.
   * - ``<additional_answer>`` (optional)
     - Specifies an additional correct answer for the problem. A problem can contain an unlimited number of additional answers. Parent: :ref:`stringresponse`. Used in :ref:`Text Input`.
   * - ``<hintgroup>`` (optional)
     - Indicates that the instructor has provided hints for certain common incorrect answers. Parent: :ref:`stringresponse`. Used in :ref:`Text Input`.
   * - ``<stringhint />`` (optional)
     - Child of ``<hintgroup>``. Specifies the text of the incorrect answer to provide the hint for. Contains answer, type, name. Used in :ref:`Text Input`.
   * - ``<hintpart>``
     - Contains the name from ``<stringhint>``. Associates the incorrect answer with the hint text for that incorrect answer. Used in :ref:`Text Input`.
   * - ``<startouttext />``
     - Indicates the beginning of the text of the hint.
   * - ``<endouttext />``
     - Indicates the end of the text of the hint.

**XML Attribute Information**

XML_Tags.rst


.. _textline:

``<textline>``
--------------

Description

Used in

:ref:`Text Input`
:ref:`Custom Python Evaluated Input`

Parent
:ref:`stringresponse`

Children

Attributes

**math** (optional): If this attribute has any value at all, a math preview will display beneath the textbox showing well-formatted math corresponding to student input.

**size** (optional): Defines the size in character widths of the input box as it is displayed to students.

**hidden** (optional): If true, the textbox will be hidden from students.