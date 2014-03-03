
.. _Appendix E:


^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
APPENDIX E: Problem and Tool XML
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This appendix provides information about the XML tags for most problem and tool types in Studio:

* :ref:`General`
* :ref:`Choice Response`
* :ref:`Chemical Equation Input`
* :ref:`Custom Response`
* :ref:`Drag and Drop`
* :ref:`Formula Response`
* :ref:`Image Response`
* :ref:`Multiple Choice Response`
* :ref:`Numerical Response`
* :ref:`Option Response`
* :ref:`Schematic Response`
* :ref:`String Response`


.. _General:

General
-------
 
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

.. _Choice Response:

Choice Response (Checkbox Problems)
-----------------------------------

**Tags**

.. list-table::
   :widths: 20 80

   * - ``<choiceresponse>``
     - Specifies that the problem lists answer options for students to choose from.
   * - ``<checkboxgroup>``
     - A child of ``<choiceresponse>``. Specifies that the problem is a checkbox problem. Can include a ``direction`` attribute and a ``label`` attribute.
   * - ``<choice>``
     - A child of ``<checkboxgroup>``. Designates an answer option. Each choice must include the ``correct`` attribute, set to ``true`` (for a correct answer) or ``false`` (for an incorrect answer). For checkbox problems, more than one option can be a correct answer.


.. _Chemical Equation Input:

Chemical Equation Input (Chemical Equation Problems)
----------------------------------------------------

**Tags**

.. list-table::
   :widths: 20 80

   * - ``<customresponse>``
     - Indicates that this problem has a custom response. The ``<customresponse>`` tags must surround the ``<chemicalequation>`` tags.
   * - ``<chemicalequationinput>``
     - A child of ``<customresponse>``. Indicates that the answer to this problem is a chemical equation. Must contain the ``size`` and ``label`` attributes.
   * - ``<answer type=loncapa/python>``
     - A child of ``<chemicalequationinput>``. Contains the Python script that grades the problem.



.. _Custom Response:

Custom Response ("Custom Python-Evaluated Input") Problems
-----------------------------------------------------------

.. list-table::
   :widths: 20 80

   * - ``<script type="loncapa/python">``
     - Indicates that the problem contains a Python script.
   * - ``<customresponse cfn="test_add_to_ten">``
     - 
   * - ``<customresponse cfn="test_add" expect="20">``
     - 
   * - <textline size="10" correct_answer="3"/>
     - This tag includes the ``size``, ``correct_answer``, and ``label`` attributes. The ``correct_answer`` attribute is optional.

.. _Drag and Drop:

Drag and Drop
-------------



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

<script>


  .. image:: ../Images/formularesponse.png


<formularesponse>


  .. image:: ../Images/formularesponse3.png

Children may include ``<formulaequationinput/>``.

If you do not need to specify any samples, you should look into the use of the
Numerical Response input type, as it provides all the capabilities of Formula
Response without the need to specify any unknown variables.

<responseparam>


  .. image:: ../Images/formularesponse6.png

<formulaequationinput/>

========= ============================================= =====
Attribute                  Description                  Notes
========= ============================================= =====
size      (optional) defines the size (i.e. the width)
          of the input box displayed to students for
          typing their math expression.
========= ============================================= =====

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

<imageresponse>

  .. image:: ../Images/imageresponse1.png

<imageinput>

  .. image:: ../Images/imageresponse2.png

.. _Multiple Choice Response:

Multiple Choice Response (Multiple Choice Problems)
-----------------------------------------------------

**XML Tags**

.. list-table::
   :widths: 20 80

   * - ``<multiplechoiceresponse>``
     - Indicates that the problem is a multiple choice problem.
   * - ``<choicegroup type="MultipleChoice">``
     - Indicates the beginning of the list of options. Contains the ``label`` attribute.
   * - ``<choice>``
     - Lists an option. This tag includes the ``correct`` and ``name`` attributes.




**XML Attribute Information**


<multiplechoiceresponse>

.. image:: ../Images/multipleresponse.png


<choicegroup>

  .. image:: ../Images/multipleresponse2.png


<choice>

  .. image:: ../Images/multipleresponse3.png

.. _Numerical Response:

Numerical Response (Numerical Input Problems)
---------------------------------------------



**XML Attribute Information**

<script>

  .. image:: ../Images/numericalresponse.png


``<numericalresponse>``

+------------+----------------------------------------------+-------------------------------+
| Attribute  |                 Description                  |              Notes            |
+============+==============================================+===============================+
| ``answer`` | A value to which student input must be       | Note that any numeric         |
|            | equivalent. Note that this expression can be | expression provided by the    |
|            | expressed in terms of a variable that is     | student will be automatically |
|            | computed in a script provided in the problem | simplified on the grader's    |
|            | by preceding the appropriate variable name   | backend.                      |
|            | with a dollar sign.                          |                               |
|            |                                              |                               |
|            | This answer will be evaluated similar to a   |                               |
|            | student's input. Thus '1/3' and 'sin(pi/5)'  |                               |
|            | are valid, as well as simpler expressions,   |                               |
|            | such as '0.3' and '42'                       |                               |
+------------+----------------------------------------------+-------------------------------+


+------------------------+--------------------------------------------+--------------------------------------+
|       Children         |                 Description                |                 Notes                |
+========================+============================================+======================================+
| ``responseparam``      | used to specify a tolerance on the accepted|                                      |
|                        | values of a number. See description below. |                                      |
+------------------------+--------------------------------------------+--------------------------------------+
|``formulaequationinput``| An input specifically for taking math      |                                      |
|                        | input from students. See below.            |                                      |
+------------------------+--------------------------------------------+--------------------------------------+
| ``textline``           | A format to take input from students, see  | Deprecated for NumericalResponse.    |
|                        | description below.                         | Use ``formulaequationinput`` instead.|
+------------------------+--------------------------------------------+--------------------------------------+


<responseparam>

  .. image:: ../Images/numericalresponse4.png

<formulaequationinput/>

========= ============================================= =====
Attribute                  Description                  Notes
========= ============================================= =====
size      (optional) defines the size (i.e. the width)
          of the input box displayed to students for
          typing their math expression.
========= ============================================= =====

<textline> (While <textline /> is supported, its use is extremely discouraged.
We urge usage of <formulaequationinput />. See the opening paragraphs of the
`Numerical Response`_ section for more information.)

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

<optionresponse>


  .. image:: ../Images/option_response1.png


<optioninput>

  .. image:: ../Images/optionresponse2.png


.. _Schematic Response:

Schematic Response (Circuit Schematic Problems)
-----------------------------------------------

The Schematic Response input type provides an interactive grid on which the
student can construct a schematic answer, such as a circuit.

**Sample Problem**

.. image:: ../Images/CircuitSchematicExample.gif
 :alt: Image of a schematic response explanation



.. _String Response:

**XML Tags**

.. list-table::
   :widths: 20 80

   * - ``<stringresponse>``
     - Indicates that the problem is a text input problem. 
   * - ``<textline>``
     - Child of ``<stringresponse>``. Lists the answer options and contains the ``label`` attribute.
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

**XML Attribute Information**

<stringresponse>

 .. raw:: html

      <table border="1" class="docutils" width="60%">
        <colgroup>
        <col width="15%">
        <col width="75%">
        <col width="10%">
        </colgroup>
        <thead valign="bottom">
        <tr class="row-odd"><th class="head">Attribute</th>
        <th class="head">Description</th>
        <th class="head">Notes</th>
        </tr>
        </thead>
        <tbody valign="top">
        <tr class="row-even"><td>type</td>
        <td>(optional) “[ci] [regex]”. Add “ci” if the student response should be graded case-insensitively. The default is to take case into consideration when grading. Add “regexp” for correct answer to be treated as regular expression.</td>
        <td>&nbsp;</td>
        </tr>
        <tr class="row-odd"><td>answer</td>
        <td>The string that is used to compare with student answer. If "regexp" is not presented in value of <em>type</em> attribute, student should enter value equal to exact value of this attribute in order to get credit. If  "regexp" is presented in value of <em>type</em> attribute, value of <em>answer</em> is treated as regular expression and exact match of this expression and student answer will be done. If search is successful, student will get credit.</td>
        <td>&nbsp;</td>
        </tr>
        </tbody>
      </table>

      <table border="1" class="docutils" width="60%">
        <colgroup>
        <col width="15%">
        <col width="75%">
        <col width="10%">
        </colgroup>
        <thead valign="bottom">
        <tr class="row-odd"><th class="head">Children</th>
        <th class="head">Description</th>
        <th class="head">Notes</th>
        </tr>
        </thead>
        <tbody valign="top">
        <tr class="row-even"><td>textline</td>
        <td>used to accept student input. See description below.</td>
        <td>&nbsp;</td>
        </tr>
        <tr class="row-odd"><td>additional_answer</td>
        <td>todo</td>
        <td>&nbsp;</td>
        </tr>
        </tbody>
      </table>


<textline>

  .. image:: ../Images/stringresponse2.png