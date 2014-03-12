
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

.. _Dropdown Problem XML:

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

.. _Numerical Input Problem XML:

===========================
Numerical Input Problem XML
===========================

Templates
---------

The following templates represent problems with and without a numerical or percentage tolerance.

Answer with no tolerance
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: xml

  <p>TEXT OF PROBLEM
      <numericalresponse answer="ANSWER (NUMBER)">
          <formulaequationinput label="TEXT OF PROBLEM"/>
      </numericalresponse>
  </p>
   
    <solution>
    <div class="detailed-solution">
    <p>TEXT OF SOLUTION</p>
    </div>
  </solution>
  </problem>

Answer with a decimal tolerance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: xml

  <problem>
   
    <p>TEXT OF PROBLEM
    <numericalresponse answer="ANSWER (NUMBER)">
      <responseparam type="tolerance" default="NUMBER (DECIMAL, e.g., .02)" />
      <formulaequationinput label="TEXT OF PROBLEM"/>
    </numericalresponse>
  </p>
   
    <solution>
    <div class="detailed-solution">
    <p>TEXT OF SOLUTION</p>
    </div>
  </solution>
  </problem>

Answer with a percentage tolerance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: xml

  <problem>
   
   <p>TEXT OF PROBLEM
    <numericalresponse answer="ANSWER (NUMBER)">
      <responseparam type="tolerance" default="NUMBER (PERCENTAGE, e.g., 3%)" />
      <formulaequationinput label="TEXT OF PROBLEM"/>
    </numericalresponse>
   </p>

    <solution>
    <div class="detailed-solution">
    <p>TEXT OF SOLUTION</p>
    </div>
  </solution>
  </problem>

Answer created with a script
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: xml

  <problem>

  <!-- Use python script spacing. The following should not be indented! -->
  <script type="loncapa/python">
  computed_response = math.sqrt(math.fsum([math.pow(math.pi,2), math.pow(math.e,2)]))
  </script>

  <p>TEXT OF PROBLEM
      <numericalresponse answer="$computed_response">
          <responseparam type="tolerance" default="0.0001" />
          <formulaequationinput label="TEXT OF PROBLEM"/>
      </numericalresponse>
  </p>

    <solution>
    <div class="detailed-solution">
     <p>TEXT OF SOLUTION</p>
    </div>
  </solution>
  </problem>

Tags
----

* ``<numericalresponse>`` (required): Specifies that the problem is a numerical input problem.
* ``<formulaequationinput>`` (required):
* ``<responseparam>`` (optional): Specifies a tolerance, or margin of error, for an answer.
* ``<script>`` (optional):

.. note:: Some older problems use the ``<textline math="1" />`` tag instead of the ``<formulaequationinput />`` tag. However, the ``<textline math="1" />`` has been deprecated. All new problems should use the ``<formulaequationinput />`` tag.

**Tag:** ``<numericalresponse>``

Specifies that the problem is a numerical input problem.

  Attributes

  .. list-table::
     :widths: 20 80

     * - Attribute
       - Description
     * - answer (required)
       - The correct answer to the problem, given as a mathematical expression. 

        .. note:: If you include a variable name preceded with a dollar sign ($) in the problem, you can include a script in the problem that computes the expression in terms of that variable.

        The grader evaluates the answer that you provide and the student's response in the same way. The grader also automatically simplifies any numeric expressions that you or a student provides. Answers can include simple expressions such as "0.3" and "42", or more complex expressions such as "1/3" and "sin(pi/5)". 

  Children

  .. list-table::
     :widths: 20 80

     * - Child
       - Description
     * - ``<responseparam>``
       - 
     * - ``<formulaequationinput>``
       - 

**Tag:** * ``<formulaequationinput>``

Creates a response field in the LMS where students enter a response.

  Attributes

  .. list-table::
     :widths: 20 80

     * - size (optional)
       - Defines the width, in characters, of the response field in the LMS.


**Tag:** ``<responseparam>``

Specifies a tolerance, or margin of error, for an answer.

  Attributes

  .. list-table::
     :widths: 20 80

     * - type (optional)
       - "tolerance": Defines a tolerance for a number
     * - default (optional)
       - A number or a percentage specifying a numerical or percent tolerance.

**Tag:** ``<script>``

Specifies a script that the grader uses to evaluate a student's response. A problem behaves as if all of the code in all of the script tags were in a single script tag. Specifically, any variables that are used in multiple ``<script>`` tags share a namespace and can be overriden.

As with all Python, indentation matters, even though the code is embedded in XML.

  Attributes

  .. list-table::
     :widths: 20 80

     * - type (required)
       - Must be set to "loncapa/python".

.. _Text Input Problem XML:

======================
Text Input Problem XML
======================

Template
--------

.. code-block:: xml

  <problem>
      <p>Problem text</p>
      <stringresponse answer="**.Correct answer 1.**" type="ci regexp">
          <additional_answer>Correct answer 2</additional_answer>
          <additional_answer>Correct answer 3</additional_answer>
          <textline size="20" label="label text"/>
          <hintgroup>
              <stringhint answer="Incorrect answer A" type="ci" name="hintA" />
                <hintpart on="hintA">
                    <startouttext />Text of hint for incorrect answer A<endouttext />
                </hintpart >
              <stringhint answer="Incorrect answer B" type="ci" name="hintB" />
                <hintpart on="hintB">
                    <startouttext />Text of hint for incorrect answer B<endouttext />
                </hintpart >
              <stringhint answer="Incorrect answer C" type="ci" name="hintC" />
                <hintpart on="hintC">
                    <startouttext />Text of hint for incorrect answer C<endouttext />
                </hintpart >
          </hintgroup>
      </stringresponse>
      <solution>
      <div class="detailed-solution">
      <p>Explanation or Solution Header</p>
      <p>Explanation or solution text</p>
      </div>
    </solution>
  </problem>

Tags
----

.. list-table::
   :widths: 20 80

   * - ``<stringresponse>``
     - Indicates that the problem is a text input problem. 
   * - ``<textline>``
     - Child of ``<stringresponse>``. Creates a response field in the LMS where the student enters a response.
   * - ``<additional_answer>`` (optional)
     - Specifies an additional correct answer for the problem. A problem can contain an unlimited number of additional answers.
   * - ``<hintgroup>`` (optional)
     - Indicates that the instructor has provided hints for certain common incorrect answers.
   * - ``<stringhint />`` (optional)
     - Child of ``<hintgroup>``. Specifies the text of the incorrect answer to provide the hint for. Contains answer, type, name.
   * - ``<hintpart>``
     - Contains the name from ``<stringhint>``. Associates the incorrect answer with the hint text for that incorrect answer.
   * - ``<startouttext />``
     - Indicates the beginning of the text of the hint.
   * - ``<endouttext />``
     - Indicates the end of the text of the hint.

**Tag:** ``<stringresponse>``

Indicates that the problem is a text input problem.

  Attributes

  .. list-table::
     :widths: 20 80

     * - Attribute
       - Description
     * - answer (required)
       - Specifies the correct answer. To designate the answer as a regular expression, add "regexp" to the **type** attribute. If you do not add "regexp" to the **type** attribute, the student's answer must match the value in this attribute exactly.
     * - type (optional)
       - Can specify whether the problem is case sensitive and allows regular expressions. If the ``<stringresponse>`` tag includes ``type="ci"``, the problem is not case sensitive. If the tag includes ``type="cs"``, the problem is case sensitive. If the tag includes ``type="regexp"``, the problem allows regular expressions. A **type** attribute in a ``<stringresponse>`` tag can also combine these values. For example, ``<stringresponse type="regexp cs">`` specifies that the prolem allows regular expressions and is case sensitive.

  Children

  .. list-table::
     :widths: 20 80

     * - Child
       - Description
     * - ``<textline />`` (required)
       - 
     * - ``<additional_answer>`` (optional)
       - 
     * - ``<hintgroup>`` (optional)
       - 

**Tag:** ``<textline />``

Creates a response field in the LMS where the student enters a response.

  Attributes

  .. list-table::
     :widths: 20 80

     * - Attribute
       - Description
     * - label (required)
       - Contains the text of the problem.
     * - size (optional)
       - Specifies the size, in characters, of the response field in the LMS.
     * - hidden
       - If set to "true", students cannot see the response field.

**Tag:** ``<additional_answer>``

Specifies an additional correct answer for the problem. A problem can contain an unlimited number of additional answers.

**Tag:** ``<hintgroup>``

Indicates that the instructor has provided hints for certain common incorrect answers.

  Children

  .. list-table::
     :widths: 20 80

     * - Child
       - Description
     * - ``<stringhint>`` (required)
       - 

**Tag:** ``<stringhint>``

Specifies a common incorrect answer to the problem.

  Attributes

  .. list-table::
     :widths: 20 80

     * - Attribute
       - Description
     * - answer (required)
       - The text of the incorrect answer.
     * - name (required)
       - The name of the hint that you want to provide.
     * - type
       - Specifies whether the text of the specified incorrect answer is case sensitive. Can be set to "cs" (case sensitive) or "ci" (case insensitive).

  Children

  .. list-table::
     :widths: 20 80

     * - Child
     * - ``<hintpart>`` (required)

**Tag:** ``<hintpart>``

Associates a common incorrect answer with the hint for that incorrect answer.

  Attributes

  .. list-table::
     :widths: 20 80

     * - Attribute
       - Description
     * - on
       - The name of the hint. This must be the same as the **name** attribute of the ``<stringhint>`` tag. (The ``<stringhint>`` tag provides the name of the hint and the incorrect answer to associate with the hint. The ``<hintpart>`` tag contains the name of the hint and the text of the hint.)

  Children

  .. list-table::
     :widths: 20 

     * - Child
     * - ``<startouttext />`` (required)
     * - ``<endouttext />`` (required)

**Tags:** ``<startouttext />`` and ``<endouttext>``

Surround the text of the hint.


.. _Drag and Drop Problem XML:

Drag and Drop XML
-----------------

For more information about how to create drag and drop problems, see `XML Format of Drag and Drop Input
<https://edx.readthedocs.org/en/latest/course_data_formats/drag_and_drop/drag_and_drop_input.html>`_.

