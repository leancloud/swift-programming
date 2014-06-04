‌‌

Summary of the Grammar 
----------------------

‌

### Statements 

Grammar of a statement

‌ statement →
[expression](Expressions.xhtml#expression);~opt~

‌ statement →
[declaration](Declarations.xhtml#declaration);~opt~

‌ statement →
[loop-statement](Statements.xhtml#loop-statement);~opt~

‌ statement →
[branch-statement](Statements.xhtml#branch-statement);~opt~

‌ statement → [labeled-statement](Statements.xhtml#labeled-statement)

‌ statement →
[control-transfer-statement](Statements.xhtml#control-transfer-statement);~opt~

‌ statements →
[statement](Statements.xhtml#statement)[statements](Statements.xhtml#statements)~opt~

Grammar of a loop statement

‌ loop-statement → [for-statement](Statements.xhtml#for-statement)

‌ loop-statement → [for-in-statement](Statements.xhtml#for-in-statement)

‌ loop-statement → [while-statement](Statements.xhtml#while-statement)

‌ loop-statement →
[do-while-statement](Statements.xhtml#do-while-statement)

Grammar of a for statement

‌ for-statement →
for[expression](Expressions.xhtml#expression)~opt~[code-block](Declarations.xhtml#code-block)

‌ for-statement →
for[code-block](Declarations.xhtml#code-block)

‌ for-init →
[variable-declaration](Declarations.xhtml#variable-declaration)
[expression-list](Expressions.xhtml#expression-list)

Grammar of a for-in statement

‌ for-in-statement →
for[expression](Expressions.xhtml#expression)[code-block](Declarations.xhtml#code-block)

Grammar of a while statement

‌ while-statement →
while[while-condition](Statements.xhtml#while-condition)[code-block](Declarations.xhtml#code-block)

‌ while-condition → [expression](Expressions.xhtml#expression)
[declaration](Declarations.xhtml#declaration)

Grammar of a do-while statement

‌ do-while-statement →
do[while-condition](Statements.xhtml#while-condition)

Grammar of a branch statement

‌ branch-statement → [if-statement](Statements.xhtml#if-statement)

‌ branch-statement →
[switch-statement](Statements.xhtml#switch-statement)

Grammar of an if statement

‌ if-statement →
if[if-condition](Statements.xhtml#if-condition)[code-block](Declarations.xhtml#code-block)[else-clause](Statements.xhtml#else-clause)~opt~

‌ if-condition → [expression](Expressions.xhtml#expression)
[declaration](Declarations.xhtml#declaration)

‌ else-clause →
else[code-block](Declarations.xhtml#code-block)
else[if-statement](Statements.xhtml#if-statement)

Grammar of a switch statement

‌ switch-statement →
switch

‌ switch-cases →
[switch-case](Statements.xhtml#switch-case)[switch-cases](Statements.xhtml#switch-cases)~opt~

‌ switch-case →
[case-label](Statements.xhtml#case-label)[statements](Statements.xhtml#statements)
[default-label](Statements.xhtml#default-label)[statements](Statements.xhtml#statements)

‌ switch-case → [case-label](Statements.xhtml#case-label);
[default-label](Statements.xhtml#default-label);

‌ case-label →
case

‌ case-item-list →
[pattern](Patterns.xhtml#pattern)[guard-clause](Statements.xhtml#guard-clause)~opt~
[pattern](Patterns.xhtml#pattern)[guard-clause](Statements.xhtml#guard-clause)~opt~,[case-item-list](Statements.xhtml#case-item-list)

‌ default-label → default

‌ guard-clause →
where[guard-expression](Statements.xhtml#guard-expression)

‌ guard-expression → [expression](Expressions.xhtml#expression)

Grammar of a labeled statement

‌ labeled-statement →
[statement-label](Statements.xhtml#statement-label)[loop-statement](Statements.xhtml#loop-statement)
[statement-label](Statements.xhtml#statement-label)[switch-statement](Statements.xhtml#switch-statement)

‌ statement-label →
[label-name](Statements.xhtml#label-name):

‌ label-name → [identifier](LexicalStructure.xhtml#identifier)

Grammar of a control transfer statement

‌ control-transfer-statement →
[break-statement](Statements.xhtml#break-statement)

‌ control-transfer-statement →
[continue-statement](Statements.xhtml#continue-statement)

‌ control-transfer-statement →
[fallthrough-statement](Statements.xhtml#fallthrough-statement)

‌ control-transfer-statement →
[return-statement](Statements.xhtml#return-statement)

Grammar of a break statement

‌ break-statement →
break[label-name](Statements.xhtml#label-name)~opt~

Grammar of a continue statement

‌ continue-statement →
continue[label-name](Statements.xhtml#label-name)~opt~

Grammar of a fallthrough statement

‌ fallthrough-statement → fallthrough

Grammar of a return statement

‌ return-statement →
return[expression](Expressions.xhtml#expression)~opt~

‌

### Generic Parameters and Arguments 

Grammar of a generic parameter clause

‌ generic-parameter-clause →
<

‌ generic-parameter-list →
[generic-parameter](GenericParametersAndArguments.xhtml#generic-parameter)
[generic-parameter](GenericParametersAndArguments.xhtml#generic-parameter),[generic-parameter-list](GenericParametersAndArguments.xhtml#generic-parameter-list)

‌ generic-parameter → [type-name](Types.xhtml#type-name)

‌ generic-parameter →
[type-name](Types.xhtml#type-name):[type-identifier](Types.xhtml#type-identifier)

‌ generic-parameter →
[type-name](Types.xhtml#type-name):[protocol-composition-type](Types.xhtml#protocol-composition-type)

‌ requirement-clause →
where[requirement-list](GenericParametersAndArguments.xhtml#requirement-list)

‌ requirement-list →
[requirement](GenericParametersAndArguments.xhtml#requirement)
[requirement](GenericParametersAndArguments.xhtml#requirement),[requirement-list](GenericParametersAndArguments.xhtml#requirement-list)

‌ requirement →
[conformance-requirement](GenericParametersAndArguments.xhtml#conformance-requirement)
[same-type-requirement](GenericParametersAndArguments.xhtml#same-type-requirement)

‌ conformance-requirement →
[type-identifier](Types.xhtml#type-identifier):[type-identifier](Types.xhtml#type-identifier)

‌ conformance-requirement →
[type-identifier](Types.xhtml#type-identifier):[protocol-composition-type](Types.xhtml#protocol-composition-type)

‌ same-type-requirement →
[type-identifier](Types.xhtml#type-identifier)==[type-identifier](Types.xhtml#type-identifier)

Grammar of a generic argument clause

‌ generic-argument-clause →
<

‌ generic-argument-list →
[generic-argument](GenericParametersAndArguments.xhtml#generic-argument)
[generic-argument](GenericParametersAndArguments.xhtml#generic-argument),[generic-argument-list](GenericParametersAndArguments.xhtml#generic-argument-list)

‌ generic-argument → [type](Types.xhtml#type)

‌

### Declarations 

Grammar of a declaration

‌ declaration →
[import-declaration](Declarations.xhtml#import-declaration)

‌ declaration →
[constant-declaration](Declarations.xhtml#constant-declaration)

‌ declaration →
[variable-declaration](Declarations.xhtml#variable-declaration)

‌ declaration →
[typealias-declaration](Declarations.xhtml#typealias-declaration)

‌ declaration →
[function-declaration](Declarations.xhtml#function-declaration)

‌ declaration → [enum-declaration](Declarations.xhtml#enum-declaration)

‌ declaration →
[struct-declaration](Declarations.xhtml#struct-declaration)

‌ declaration →
[class-declaration](Declarations.xhtml#class-declaration)

‌ declaration →
[protocol-declaration](Declarations.xhtml#protocol-declaration)

‌ declaration →
[initializer-declaration](Declarations.xhtml#initializer-declaration)

‌ declaration →
[deinitializer-declaration](Declarations.xhtml#deinitializer-declaration)

‌ declaration →
[extension-declaration](Declarations.xhtml#extension-declaration)

‌ declaration →
[subscript-declaration](Declarations.xhtml#subscript-declaration)

‌ declaration →
[operator-declaration](Declarations.xhtml#operator-declaration)

‌ declarations →
[declaration](Declarations.xhtml#declaration)[declarations](Declarations.xhtml#declarations)~opt~

‌ declaration-specifiers →
[declaration-specifier](Declarations.xhtml#declaration-specifier)[declaration-specifiers](Declarations.xhtml#declaration-specifiers)~opt~

‌ declaration-specifier → class
nonmutating
unowned
unowned(unsafe)

Grammar of a top-level declaration

‌ top-level-declaration → [statements](Statements.xhtml#statements)~opt~

Grammar of a code block

‌ code-block →


Grammar of an import declaration

‌ import-declaration →
[attributes](Attributes.xhtml#attributes)~opt~import[import-kind](Declarations.xhtml#import-kind)~opt~[import-path](Declarations.xhtml#import-path)

‌ import-kind → typealias
class
func

‌ import-path →
[import-path-identifier](Declarations.xhtml#import-path-identifier)
[import-path-identifier](Declarations.xhtml#import-path-identifier).[import-path](Declarations.xhtml#import-path)

‌ import-path-identifier →
[identifier](LexicalStructure.xhtml#identifier)
[operator](LexicalStructure.xhtml#operator)

Grammar of a constant declaration

‌ constant-declaration →
[attributes](Attributes.xhtml#attributes)~opt~[declaration-specifiers](Declarations.xhtml#declaration-specifiers)~opt~let[pattern-initializer-list](Declarations.xhtml#pattern-initializer-list)

‌ pattern-initializer-list →
[pattern-initializer](Declarations.xhtml#pattern-initializer)
[pattern-initializer](Declarations.xhtml#pattern-initializer),[pattern-initializer-list](Declarations.xhtml#pattern-initializer-list)

‌ pattern-initializer →
[pattern](Patterns.xhtml#pattern)[initializer](Declarations.xhtml#initializer)~opt~

‌ initializer → =[expression](Expressions.xhtml#expression)

Grammar of a variable declaration

‌ variable-declaration →
[variable-declaration-head](Declarations.xhtml#variable-declaration-head)[pattern-initializer-list](Declarations.xhtml#pattern-initializer-list)

‌ variable-declaration →
[variable-declaration-head](Declarations.xhtml#variable-declaration-head)[variable-name](Declarations.xhtml#variable-name)[type-annotation](Types.xhtml#type-annotation)[code-block](Declarations.xhtml#code-block)

‌ variable-declaration →
[variable-declaration-head](Declarations.xhtml#variable-declaration-head)[variable-name](Declarations.xhtml#variable-name)[type-annotation](Types.xhtml#type-annotation)[getter-setter-block](Declarations.xhtml#getter-setter-block)

‌ variable-declaration →
[variable-declaration-head](Declarations.xhtml#variable-declaration-head)[variable-name](Declarations.xhtml#variable-name)[type-annotation](Types.xhtml#type-annotation)[getter-setter-keyword-block](Declarations.xhtml#getter-setter-keyword-block)

‌ variable-declaration →
[variable-declaration-head](Declarations.xhtml#variable-declaration-head)[variable-name](Declarations.xhtml#variable-name)[type-annotation](Types.xhtml#type-annotation)[initializer](Declarations.xhtml#initializer)~opt~[willSet-didSet-block](Declarations.xhtml#willSet-didSet-block)

‌ variable-declaration-head →
[attributes](Attributes.xhtml#attributes)~opt~[declaration-specifiers](Declarations.xhtml#declaration-specifiers)~opt~var

‌ variable-name → [identifier](LexicalStructure.xhtml#identifier)

‌ getter-setter-block →


‌ getter-setter-block →


‌ getter-clause →
[attributes](Attributes.xhtml#attributes)~opt~get[code-block](Declarations.xhtml#code-block)

‌ setter-clause →
[attributes](Attributes.xhtml#attributes)~opt~set[setter-name](Declarations.xhtml#setter-name)~opt~[code-block](Declarations.xhtml#code-block)

‌ setter-name →
(

‌ getter-setter-keyword-block →


‌ getter-setter-keyword-block →


‌ getter-keyword-clause →
[attributes](Attributes.xhtml#attributes)~opt~get

‌ setter-keyword-clause →
[attributes](Attributes.xhtml#attributes)~opt~set

‌ willSet-didSet-block →


‌ willSet-didSet-block →


‌ willSet-clause →
[attributes](Attributes.xhtml#attributes)~opt~willSet[setter-name](Declarations.xhtml#setter-name)~opt~[code-block](Declarations.xhtml#code-block)

‌ didSet-clause →
[attributes](Attributes.xhtml#attributes)~opt~didSet[setter-name](Declarations.xhtml#setter-name)~opt~[code-block](Declarations.xhtml#code-block)

Grammar of a type alias declaration

‌ typealias-declaration →
[typealias-head](Declarations.xhtml#typealias-head)[typealias-assignment](Declarations.xhtml#typealias-assignment)

‌ typealias-head →
typealias[typealias-name](Declarations.xhtml#typealias-name)

‌ typealias-name → [identifier](LexicalStructure.xhtml#identifier)

‌ typealias-assignment → =[type](Types.xhtml#type)

Grammar of a function declaration

‌ function-declaration →
[function-head](Declarations.xhtml#function-head)[function-name](Declarations.xhtml#function-name)[generic-parameter-clause](GenericParametersAndArguments.xhtml#generic-parameter-clause)~opt~[function-signature](Declarations.xhtml#function-signature)[function-body](Declarations.xhtml#function-body)

‌ function-head →
[attributes](Attributes.xhtml#attributes)~opt~[declaration-specifiers](Declarations.xhtml#declaration-specifiers)~opt~func

‌ function-name → [identifier](LexicalStructure.xhtml#identifier)
[operator](LexicalStructure.xhtml#operator)

‌ function-signature →
[parameter-clauses](Declarations.xhtml#parameter-clauses)[function-result](Declarations.xhtml#function-result)~opt~

‌ function-result →
->[attributes](Attributes.xhtml#attributes)~opt~[type](Types.xhtml#type)

‌ function-body → [code-block](Declarations.xhtml#code-block)

‌ parameter-clauses →
[parameter-clause](Declarations.xhtml#parameter-clause)[parameter-clauses](Declarations.xhtml#parameter-clauses)~opt~

‌ parameter-clause → (
(

‌ parameter-list → [parameter](Declarations.xhtml#parameter)
[parameter](Declarations.xhtml#parameter),[parameter-list](Declarations.xhtml#parameter-list)

‌ parameter →
inout~opt~[parameter-name](Declarations.xhtml#parameter-name)[local-parameter-name](Declarations.xhtml#local-parameter-name)~opt~[type-annotation](Types.xhtml#type-annotation)[default-argument-clause](Declarations.xhtml#default-argument-clause)~opt~

‌ parameter →
inout~opt~[parameter-name](Declarations.xhtml#parameter-name)[local-parameter-name](Declarations.xhtml#local-parameter-name)~opt~[type-annotation](Types.xhtml#type-annotation)[default-argument-clause](Declarations.xhtml#default-argument-clause)~opt~

‌ parameter →
[attributes](Attributes.xhtml#attributes)~opt~[type](Types.xhtml#type)

‌ parameter-name → [identifier](LexicalStructure.xhtml#identifier)
_

‌ local-parameter-name → [identifier](LexicalStructure.xhtml#identifier)
_

‌ default-argument-clause →
=[expression](Expressions.xhtml#expression)

Grammar of an enumeration declaration

‌ enum-declaration →
[attributes](Attributes.xhtml#attributes)~opt~[union-style-enum](Declarations.xhtml#union-style-enum)
[attributes](Attributes.xhtml#attributes)~opt~[raw-value-style-enum](Declarations.xhtml#raw-value-style-enum)

‌ union-style-enum →
[enum-name](Declarations.xhtml#enum-name)[generic-parameter-clause](GenericParametersAndArguments.xhtml#generic-parameter-clause)~opt~

‌ union-style-enum-members →
[union-style-enum-member](Declarations.xhtml#union-style-enum-member)[union-style-enum-members](Declarations.xhtml#union-style-enum-members)~opt~

‌ union-style-enum-member →
[declaration](Declarations.xhtml#declaration)
[union-style-enum-case-clause](Declarations.xhtml#union-style-enum-case-clause)

‌ union-style-enum-case-clause →
[attributes](Attributes.xhtml#attributes)~opt~case[union-style-enum-case-list](Declarations.xhtml#union-style-enum-case-list)

‌ union-style-enum-case-list →
[union-style-enum-case](Declarations.xhtml#union-style-enum-case)
[union-style-enum-case](Declarations.xhtml#union-style-enum-case),[union-style-enum-case-list](Declarations.xhtml#union-style-enum-case-list)

‌ union-style-enum-case →
[enum-case-name](Declarations.xhtml#enum-case-name)[tuple-type](Types.xhtml#tuple-type)~opt~

‌ enum-name → [identifier](LexicalStructure.xhtml#identifier)

‌ enum-case-name → [identifier](LexicalStructure.xhtml#identifier)

‌ raw-value-style-enum →
[enum-name](Declarations.xhtml#enum-name)[generic-parameter-clause](GenericParametersAndArguments.xhtml#generic-parameter-clause)~opt~:

‌ raw-value-style-enum-members →
[raw-value-style-enum-member](Declarations.xhtml#raw-value-style-enum-member)[raw-value-style-enum-members](Declarations.xhtml#raw-value-style-enum-members)~opt~

‌ raw-value-style-enum-member →
[declaration](Declarations.xhtml#declaration)
[raw-value-style-enum-case-clause](Declarations.xhtml#raw-value-style-enum-case-clause)

‌ raw-value-style-enum-case-clause →
[attributes](Attributes.xhtml#attributes)~opt~case[raw-value-style-enum-case-list](Declarations.xhtml#raw-value-style-enum-case-list)

‌ raw-value-style-enum-case-list →
[raw-value-style-enum-case](Declarations.xhtml#raw-value-style-enum-case)
[raw-value-style-enum-case](Declarations.xhtml#raw-value-style-enum-case),[raw-value-style-enum-case-list](Declarations.xhtml#raw-value-style-enum-case-list)

‌ raw-value-style-enum-case →
[enum-case-name](Declarations.xhtml#enum-case-name)[raw-value-assignment](Declarations.xhtml#raw-value-assignment)~opt~

‌ raw-value-assignment →
=[literal](LexicalStructure.xhtml#literal)

Grammar of a structure declaration

‌ struct-declaration →
[attributes](Attributes.xhtml#attributes)~opt~struct[struct-name](Declarations.xhtml#struct-name)[generic-parameter-clause](GenericParametersAndArguments.xhtml#generic-parameter-clause)~opt~[type-inheritance-clause](Types.xhtml#type-inheritance-clause)~opt~[struct-body](Declarations.xhtml#struct-body)

‌ struct-name → [identifier](LexicalStructure.xhtml#identifier)

‌ struct-body →


Grammar of a class declaration

‌ class-declaration →
[attributes](Attributes.xhtml#attributes)~opt~class[class-name](Declarations.xhtml#class-name)[generic-parameter-clause](GenericParametersAndArguments.xhtml#generic-parameter-clause)~opt~[type-inheritance-clause](Types.xhtml#type-inheritance-clause)~opt~[class-body](Declarations.xhtml#class-body)

‌ class-name → [identifier](LexicalStructure.xhtml#identifier)

‌ class-body →


Grammar of a protocol declaration

‌ protocol-declaration →
[attributes](Attributes.xhtml#attributes)~opt~protocol[protocol-name](Declarations.xhtml#protocol-name)[type-inheritance-clause](Types.xhtml#type-inheritance-clause)~opt~[protocol-body](Declarations.xhtml#protocol-body)

‌ protocol-name → [identifier](LexicalStructure.xhtml#identifier)

‌ protocol-body →


‌ protocol-member-declaration →
[protocol-property-declaration](Declarations.xhtml#protocol-property-declaration)

‌ protocol-member-declaration →
[protocol-method-declaration](Declarations.xhtml#protocol-method-declaration)

‌ protocol-member-declaration →
[protocol-initializer-declaration](Declarations.xhtml#protocol-initializer-declaration)

‌ protocol-member-declaration →
[protocol-subscript-declaration](Declarations.xhtml#protocol-subscript-declaration)

‌ protocol-member-declaration →
[protocol-associated-type-declaration](Declarations.xhtml#protocol-associated-type-declaration)

‌ protocol-member-declarations →
[protocol-member-declaration](Declarations.xhtml#protocol-member-declaration)[protocol-member-declarations](Declarations.xhtml#protocol-member-declarations)~opt~

Grammar of a protocol property declaration

‌ protocol-property-declaration →
[variable-declaration-head](Declarations.xhtml#variable-declaration-head)[variable-name](Declarations.xhtml#variable-name)[type-annotation](Types.xhtml#type-annotation)[getter-setter-keyword-block](Declarations.xhtml#getter-setter-keyword-block)

Grammar of a protocol method declaration

‌ protocol-method-declaration →
[function-head](Declarations.xhtml#function-head)[function-name](Declarations.xhtml#function-name)[generic-parameter-clause](GenericParametersAndArguments.xhtml#generic-parameter-clause)~opt~[function-signature](Declarations.xhtml#function-signature)

Grammar of a protocol initializer declaration

‌ protocol-initializer-declaration →
[initializer-head](Declarations.xhtml#initializer-head)[generic-parameter-clause](GenericParametersAndArguments.xhtml#generic-parameter-clause)~opt~[parameter-clause](Declarations.xhtml#parameter-clause)

Grammar of a protocol subscript declaration

‌ protocol-subscript-declaration →
[subscript-head](Declarations.xhtml#subscript-head)[subscript-result](Declarations.xhtml#subscript-result)[getter-setter-keyword-block](Declarations.xhtml#getter-setter-keyword-block)

Grammar of a protocol associated type declaration

‌ protocol-associated-type-declaration →
[typealias-head](Declarations.xhtml#typealias-head)[type-inheritance-clause](Types.xhtml#type-inheritance-clause)~opt~[typealias-assignment](Declarations.xhtml#typealias-assignment)~opt~

Grammar of an initializer declaration

‌ initializer-declaration →
[initializer-head](Declarations.xhtml#initializer-head)[generic-parameter-clause](GenericParametersAndArguments.xhtml#generic-parameter-clause)~opt~[parameter-clause](Declarations.xhtml#parameter-clause)[initializer-body](Declarations.xhtml#initializer-body)

‌ initializer-head →
[attributes](Attributes.xhtml#attributes)~opt~convenience

‌ initializer-body → [code-block](Declarations.xhtml#code-block)

Grammar of a deinitializer declaration

‌ deinitializer-declaration →
[attributes](Attributes.xhtml#attributes)~opt~deinit[code-block](Declarations.xhtml#code-block)

Grammar of an extension declaration

‌ extension-declaration →
extension[type-identifier](Types.xhtml#type-identifier)[type-inheritance-clause](Types.xhtml#type-inheritance-clause)~opt~[extension-body](Declarations.xhtml#extension-body)

‌ extension-body →


Grammar of a subscript declaration

‌ subscript-declaration →
[subscript-head](Declarations.xhtml#subscript-head)[subscript-result](Declarations.xhtml#subscript-result)[code-block](Declarations.xhtml#code-block)

‌ subscript-declaration →
[subscript-head](Declarations.xhtml#subscript-head)[subscript-result](Declarations.xhtml#subscript-result)[getter-setter-block](Declarations.xhtml#getter-setter-block)

‌ subscript-declaration →
[subscript-head](Declarations.xhtml#subscript-head)[subscript-result](Declarations.xhtml#subscript-result)[getter-setter-keyword-block](Declarations.xhtml#getter-setter-keyword-block)

‌ subscript-head →
[attributes](Attributes.xhtml#attributes)~opt~subscript[parameter-clause](Declarations.xhtml#parameter-clause)

‌ subscript-result →
->[attributes](Attributes.xhtml#attributes)~opt~[type](Types.xhtml#type)

Grammar of an operator declaration

‌ operator-declaration →
[prefix-operator-declaration](Declarations.xhtml#prefix-operator-declaration)
[postfix-operator-declaration](Declarations.xhtml#postfix-operator-declaration)
[infix-operator-declaration](Declarations.xhtml#infix-operator-declaration)

‌ prefix-operator-declaration →
operator

‌ postfix-operator-declaration →
operator

‌ infix-operator-declaration →
operator

‌ infix-operator-attributes →
[precedence-clause](Declarations.xhtml#precedence-clause)~opt~[associativity-clause](Declarations.xhtml#associativity-clause)~opt~

‌ precedence-clause →
precedence[precedence-level](Declarations.xhtml#precedence-level)

‌ precedence-level → Digit 0 through 255

‌ associativity-clause →
associativity[associativity](Declarations.xhtml#associativity)

‌ associativity → left

‌

### Patterns 

Grammar of a pattern

‌ pattern →
[wildcard-pattern](Patterns.xhtml#wildcard-pattern)[type-annotation](Types.xhtml#type-annotation)~opt~

‌ pattern →
[identifier-pattern](Patterns.xhtml#identifier-pattern)[type-annotation](Types.xhtml#type-annotation)~opt~

‌ pattern →
[value-binding-pattern](Patterns.xhtml#value-binding-pattern)

‌ pattern →
[tuple-pattern](Patterns.xhtml#tuple-pattern)[type-annotation](Types.xhtml#type-annotation)~opt~

‌ pattern → [enum-case-pattern](Patterns.xhtml#enum-case-pattern)

‌ pattern → [type-casting-pattern](Patterns.xhtml#type-casting-pattern)

‌ pattern → [expression-pattern](Patterns.xhtml#expression-pattern)

Grammar of a wildcard pattern

‌ wildcard-pattern → _

Grammar of an identifier pattern

‌ identifier-pattern → [identifier](LexicalStructure.xhtml#identifier)

Grammar of a value-binding pattern

‌ value-binding-pattern →
var[pattern](Patterns.xhtml#pattern)
let[pattern](Patterns.xhtml#pattern)

Grammar of a tuple pattern

‌ tuple-pattern →
(

‌ tuple-pattern-element-list →
[tuple-pattern-element](Patterns.xhtml#tuple-pattern-element)
[tuple-pattern-element](Patterns.xhtml#tuple-pattern-element),[tuple-pattern-element-list](Patterns.xhtml#tuple-pattern-element-list)

‌ tuple-pattern-element → [pattern](Patterns.xhtml#pattern)

Grammar of an enumeration case pattern

‌ enum-case-pattern →
[type-identifier](Types.xhtml#type-identifier)~opt~.[enum-case-name](Declarations.xhtml#enum-case-name)[tuple-pattern](Patterns.xhtml#tuple-pattern)~opt~

Grammar of a type casting pattern

‌ type-casting-pattern → [is-pattern](Patterns.xhtml#is-pattern)
[as-pattern](Patterns.xhtml#as-pattern)

‌ is-pattern → is[type](Types.xhtml#type)

‌ as-pattern →
[pattern](Patterns.xhtml#pattern)as[type](Types.xhtml#type)

Grammar of an expression pattern

‌ expression-pattern → [expression](Expressions.xhtml#expression)

‌

### Attributes 

Grammar of an attribute

‌ attribute →
@[attribute-name](Attributes.xhtml#attribute-name)[attribute-argument-clause](Attributes.xhtml#attribute-argument-clause)~opt~

‌ attribute-name → [identifier](LexicalStructure.xhtml#identifier)

‌ attribute-argument-clause →
(

‌ attributes →
[attribute](Attributes.xhtml#attribute)[attributes](Attributes.xhtml#attributes)~opt~

‌ balanced-tokens →
[balanced-token](Attributes.xhtml#balanced-token)[balanced-tokens](Attributes.xhtml#balanced-tokens)~opt~

‌ balanced-token →
(

‌ balanced-token →
[

‌ balanced-token →


‌ balanced-token → Any identifier, keyword, literal, or operator

‌ balanced-token → Any punctuation except (,
[

‌

### Expressions 

Grammar of an expression

‌ expression →
[prefix-expression](Expressions.xhtml#prefix-expression)[binary-expressions](Expressions.xhtml#binary-expressions)~opt~

‌ expression-list → [expression](Expressions.xhtml#expression)
[expression](Expressions.xhtml#expression),[expression-list](Expressions.xhtml#expression-list)

Grammar of a prefix expression

‌ prefix-expression →
[prefix-operator](LexicalStructure.xhtml#prefix-operator)~opt~[postfix-expression](Expressions.xhtml#postfix-expression)

‌ prefix-expression →
[in-out-expression](Expressions.xhtml#in-out-expression)

‌ in-out-expression →
&[identifier](LexicalStructure.xhtml#identifier)

Grammar of a binary expression

‌ binary-expression →
[binary-operator](LexicalStructure.xhtml#binary-operator)[prefix-expression](Expressions.xhtml#prefix-expression)

‌ binary-expression →
[assignment-operator](Expressions.xhtml#assignment-operator)[prefix-expression](Expressions.xhtml#prefix-expression)

‌ binary-expression →
[conditional-operator](Expressions.xhtml#conditional-operator)[prefix-expression](Expressions.xhtml#prefix-expression)

‌ binary-expression →
[type-casting-operator](Expressions.xhtml#type-casting-operator)

‌ binary-expressions →
[binary-expression](Expressions.xhtml#binary-expression)[binary-expressions](Expressions.xhtml#binary-expressions)~opt~

Grammar of an assignment operator

‌ assignment-operator → =

Grammar of a conditional operator

‌ conditional-operator →
?

Grammar of a type-casting operator

‌ type-casting-operator → is[type](Types.xhtml#type)
as~opt~[type](Types.xhtml#type)

Grammar of a primary expression

‌ primary-expression →
[identifier](LexicalStructure.xhtml#identifier)[generic-argument-clause](GenericParametersAndArguments.xhtml#generic-argument-clause)~opt~

‌ primary-expression →
[literal-expression](Expressions.xhtml#literal-expression)

‌ primary-expression →
[self-expression](Expressions.xhtml#self-expression)

‌ primary-expression →
[superclass-expression](Expressions.xhtml#superclass-expression)

‌ primary-expression →
[closure-expression](Expressions.xhtml#closure-expression)

‌ primary-expression →
[parenthesized-expression](Expressions.xhtml#parenthesized-expression)

‌ primary-expression →
[implicit-member-expression](Expressions.xhtml#implicit-member-expression)

‌ primary-expression →
[wildcard-expression](Expressions.xhtml#wildcard-expression)

Grammar of a literal expression

‌ literal-expression → [literal](LexicalStructure.xhtml#literal)

‌ literal-expression → [array-literal](Expressions.xhtml#array-literal)
[dictionary-literal](Expressions.xhtml#dictionary-literal)

‌ literal-expression → __FILE__
__COLUMN__

‌ array-literal →
[

‌ array-literal-items →
[array-literal-item](Expressions.xhtml#array-literal-item),~opt~
[array-literal-item](Expressions.xhtml#array-literal-item),[array-literal-items](Expressions.xhtml#array-literal-items)

‌ array-literal-item → [expression](Expressions.xhtml#expression)

‌ dictionary-literal →
[
[

‌ dictionary-literal-items →
[dictionary-literal-item](Expressions.xhtml#dictionary-literal-item),~opt~
[dictionary-literal-item](Expressions.xhtml#dictionary-literal-item),[dictionary-literal-items](Expressions.xhtml#dictionary-literal-items)

‌ dictionary-literal-item →
[expression](Expressions.xhtml#expression):[expression](Expressions.xhtml#expression)

Grammar of a self expression

‌ self-expression → self

‌ self-expression →
self[identifier](LexicalStructure.xhtml#identifier)

‌ self-expression →
self

‌ self-expression → self

Grammar of a superclass expression

‌ superclass-expression →
[superclass-method-expression](Expressions.xhtml#superclass-method-expression)
[superclass-subscript-expression](Expressions.xhtml#superclass-subscript-expression)
[superclass-initializer-expression](Expressions.xhtml#superclass-initializer-expression)

‌ superclass-method-expression →
super[identifier](LexicalStructure.xhtml#identifier)

‌ superclass-subscript-expression →
super

‌ superclass-initializer-expression →
super

Grammar of a closure expression

‌ closure-expression →


‌ closure-signature →
[parameter-clause](Declarations.xhtml#parameter-clause)[function-result](Declarations.xhtml#function-result)~opt~in

‌ closure-signature →
[identifier-list](LexicalStructure.xhtml#identifier-list)[function-result](Declarations.xhtml#function-result)~opt~in

‌ closure-signature →
[capture-list](Expressions.xhtml#capture-list)[parameter-clause](Declarations.xhtml#parameter-clause)[function-result](Declarations.xhtml#function-result)~opt~in

‌ closure-signature →
[capture-list](Expressions.xhtml#capture-list)[identifier-list](LexicalStructure.xhtml#identifier-list)[function-result](Declarations.xhtml#function-result)~opt~in

‌ closure-signature →
[capture-list](Expressions.xhtml#capture-list)in

‌ capture-list →
[

‌ capture-specifier → weak
unowned(safe)

Grammar of a implicit member expression

‌ implicit-member-expression →
.[identifier](LexicalStructure.xhtml#identifier)

Grammar of a parenthesized expression

‌ parenthesized-expression →
(

‌ expression-element-list →
[expression-element](Expressions.xhtml#expression-element)
[expression-element](Expressions.xhtml#expression-element),[expression-element-list](Expressions.xhtml#expression-element-list)

‌ expression-element → [expression](Expressions.xhtml#expression)
[identifier](LexicalStructure.xhtml#identifier):[expression](Expressions.xhtml#expression)

Grammar of a wildcard expression

‌ wildcard-expression → _

Grammar of a postfix expression

‌ postfix-expression →
[primary-expression](Expressions.xhtml#primary-expression)

‌ postfix-expression →
[postfix-expression](Expressions.xhtml#postfix-expression)[postfix-operator](LexicalStructure.xhtml#postfix-operator)

‌ postfix-expression →
[function-call-expression](Expressions.xhtml#function-call-expression)

‌ postfix-expression →
[initializer-expression](Expressions.xhtml#initializer-expression)

‌ postfix-expression →
[explicit-member-expression](Expressions.xhtml#explicit-member-expression)

‌ postfix-expression →
[postfix-self-expression](Expressions.xhtml#postfix-self-expression)

‌ postfix-expression →
[dynamic-type-expression](Expressions.xhtml#dynamic-type-expression)

‌ postfix-expression →
[subscript-expression](Expressions.xhtml#subscript-expression)

‌ postfix-expression →
[forced-value-expression](Expressions.xhtml#forced-value-expression)

‌ postfix-expression →
[optional-chaining-expression](Expressions.xhtml#optional-chaining-expression)

Grammar of a function call expression

‌ function-call-expression →
[postfix-expression](Expressions.xhtml#postfix-expression)[parenthesized-expression](Expressions.xhtml#parenthesized-expression)

‌ function-call-expression →
[postfix-expression](Expressions.xhtml#postfix-expression)[parenthesized-expression](Expressions.xhtml#parenthesized-expression)~opt~[trailing-closure](Expressions.xhtml#trailing-closure)

‌ trailing-closure →
[closure-expression](Expressions.xhtml#closure-expression)

Grammar of an initializer expression

‌ initializer-expression →
[postfix-expression](Expressions.xhtml#postfix-expression).

Grammar of an explicit member expression

‌ explicit-member-expression →
[postfix-expression](Expressions.xhtml#postfix-expression).[decimal-digit](LexicalStructure.xhtml#decimal-digit)

‌ explicit-member-expression →
[postfix-expression](Expressions.xhtml#postfix-expression).[identifier](LexicalStructure.xhtml#identifier)[generic-argument-clause](GenericParametersAndArguments.xhtml#generic-argument-clause)~opt~

Grammar of a self expression

‌ postfix-self-expression →
[postfix-expression](Expressions.xhtml#postfix-expression).

Grammar of a dynamic type expression

‌ dynamic-type-expression →
[postfix-expression](Expressions.xhtml#postfix-expression).

Grammar of a subscript expression

‌ subscript-expression →
[postfix-expression](Expressions.xhtml#postfix-expression)[

Grammar of a forced-value expression

‌ forced-value-expression →
[postfix-expression](Expressions.xhtml#postfix-expression)!

Grammar of an optional-chaining expression

‌ optional-chaining-expression →
[postfix-expression](Expressions.xhtml#postfix-expression)?

‌

### Lexical Structure 

Grammar of an identifier

‌ identifier →
[identifier-head](LexicalStructure.xhtml#identifier-head)[identifier-characters](LexicalStructure.xhtml#identifier-characters)~opt~

‌ identifier →
  

‌ identifier →
[implicit-parameter-name](LexicalStructure.xhtml#implicit-parameter-name)

‌ identifier-list → [identifier](LexicalStructure.xhtml#identifier)
[identifier](LexicalStructure.xhtml#identifier),[identifier-list](LexicalStructure.xhtml#identifier-list)

‌ identifier-head → Upper- or lowercase letter A through Z

‌ identifier-head → U+00A8, U+00AA, U+00AD, U+00AF, U+00B2–U+00B5, or
U+00B7–U+00BA

‌ identifier-head → U+00BC–U+00BE, U+00C0–U+00D6, U+00D8–U+00F6, or
U+00F8–U+00FF

‌ identifier-head → U+0100–U+02FF, U+0370–U+167F, U+1681–U+180D, or
U+180F–U+1DBF

‌ identifier-head → U+1E00–U+1FFF

‌ identifier-head → U+200B–U+200D, U+202A–U+202E, U+203F–U+2040, U+2054,
or U+2060–U+206F

‌ identifier-head → U+2070–U+20CF, U+2100–U+218F, U+2460–U+24FF, or
U+2776–U+2793

‌ identifier-head → U+2C00–U+2DFF or U+2E80–U+2FFF

‌ identifier-head → U+3004–U+3007, U+3021–U+302F, U+3031–U+303F, or
U+3040–U+D7FF

‌ identifier-head → U+F900–U+FD3D, U+FD40–U+FDCF, U+FDF0–U+FE1F, or
U+FE30–U+FE44

‌ identifier-head → U+FE47–U+FFFD

‌ identifier-head → U+10000–U+1FFFD, U+20000–U+2FFFD, U+30000–U+3FFFD,
or U+40000–U+4FFFD

‌ identifier-head → U+50000–U+5FFFD, U+60000–U+6FFFD, U+70000–U+7FFFD,
or U+80000–U+8FFFD

‌ identifier-head → U+90000–U+9FFFD, U+A0000–U+AFFFD, U+B0000–U+BFFFD,
or U+C0000–U+CFFFD

‌ identifier-head → U+D0000–U+DFFFD or U+E0000–U+EFFFD

‌ identifier-character → Digit 0 through 9

‌ identifier-character → U+0300–U+036F, U+1DC0–U+1DFF, U+20D0–U+20FF, or
U+FE20–U+FE2F

‌ identifier-character →
[identifier-head](LexicalStructure.xhtml#identifier-head)

‌ identifier-characters →
[identifier-character](LexicalStructure.xhtml#identifier-character)[identifier-characters](LexicalStructure.xhtml#identifier-characters)~opt~

‌ implicit-parameter-name →
$[decimal-digits](LexicalStructure.xhtml#decimal-digits)

Grammar of a literal

‌ literal → [integer-literal](LexicalStructure.xhtml#integer-literal)
[floating-point-literal](LexicalStructure.xhtml#floating-point-literal)
[string-literal](LexicalStructure.xhtml#string-literal)

Grammar of an integer literal

‌ integer-literal →
[binary-literal](LexicalStructure.xhtml#binary-literal)

‌ integer-literal →
[octal-literal](LexicalStructure.xhtml#octal-literal)

‌ integer-literal →
[decimal-literal](LexicalStructure.xhtml#decimal-literal)

‌ integer-literal →
[hexadecimal-literal](LexicalStructure.xhtml#hexadecimal-literal)

‌ binary-literal →
0b[binary-digit](LexicalStructure.xhtml#binary-digit)[binary-literal-characters](LexicalStructure.xhtml#binary-literal-characters)~opt~

‌ binary-digit → Digit 0 or 1

‌ binary-literal-character →
[binary-digit](LexicalStructure.xhtml#binary-digit) _

‌ binary-literal-characters →
[binary-literal-character](LexicalStructure.xhtml#binary-literal-character)[binary-literal-characters](LexicalStructure.xhtml#binary-literal-characters)~opt~

‌ octal-literal →
0o[octal-digit](LexicalStructure.xhtml#octal-digit)[octal-literal-characters](LexicalStructure.xhtml#octal-literal-characters)~opt~

‌ octal-digit → Digit 0 through 7

‌ octal-literal-character →
[octal-digit](LexicalStructure.xhtml#octal-digit) _

‌ octal-literal-characters →
[octal-literal-character](LexicalStructure.xhtml#octal-literal-character)[octal-literal-characters](LexicalStructure.xhtml#octal-literal-characters)~opt~

‌ decimal-literal →
[decimal-digit](LexicalStructure.xhtml#decimal-digit)[decimal-literal-characters](LexicalStructure.xhtml#decimal-literal-characters)~opt~

‌ decimal-digit → Digit 0 through 9

‌ decimal-digits →
[decimal-digit](LexicalStructure.xhtml#decimal-digit)[decimal-digits](LexicalStructure.xhtml#decimal-digits)~opt~

‌ decimal-literal-character →
[decimal-digit](LexicalStructure.xhtml#decimal-digit) _

‌ decimal-literal-characters →
[decimal-literal-character](LexicalStructure.xhtml#decimal-literal-character)[decimal-literal-characters](LexicalStructure.xhtml#decimal-literal-characters)~opt~

‌ hexadecimal-literal →
0x[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-literal-characters](LexicalStructure.xhtml#hexadecimal-literal-characters)~opt~

‌ hexadecimal-digit → Digit 0 through 9, a through f, or A through F

‌ hexadecimal-literal-character →
[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)
_

‌ hexadecimal-literal-characters →
[hexadecimal-literal-character](LexicalStructure.xhtml#hexadecimal-literal-character)[hexadecimal-literal-characters](LexicalStructure.xhtml#hexadecimal-literal-characters)~opt~

Grammar of a floating-point literal

‌ floating-point-literal →
[decimal-literal](LexicalStructure.xhtml#decimal-literal)[decimal-fraction](LexicalStructure.xhtml#decimal-fraction)~opt~[decimal-exponent](LexicalStructure.xhtml#decimal-exponent)~opt~

‌ floating-point-literal →
[hexadecimal-literal](LexicalStructure.xhtml#hexadecimal-literal)[hexadecimal-fraction](LexicalStructure.xhtml#hexadecimal-fraction)~opt~[hexadecimal-exponent](LexicalStructure.xhtml#hexadecimal-exponent)

‌ decimal-fraction →
.[decimal-literal](LexicalStructure.xhtml#decimal-literal)

‌ decimal-exponent →
[floating-point-e](LexicalStructure.xhtml#floating-point-e)[sign](LexicalStructure.xhtml#sign)~opt~[decimal-literal](LexicalStructure.xhtml#decimal-literal)

‌ hexadecimal-fraction →
.[hexadecimal-literal](LexicalStructure.xhtml#hexadecimal-literal)~opt~

‌ hexadecimal-exponent →
[floating-point-p](LexicalStructure.xhtml#floating-point-p)[sign](LexicalStructure.xhtml#sign)~opt~[hexadecimal-literal](LexicalStructure.xhtml#hexadecimal-literal)

‌ floating-point-e → e

‌ floating-point-p → p

‌ sign → +

Grammar of a string literal

‌ string-literal →
"

‌ quoted-text →
[quoted-text-item](LexicalStructure.xhtml#quoted-text-item)[quoted-text](LexicalStructure.xhtml#quoted-text)~opt~

‌ quoted-text-item →
[escaped-character](LexicalStructure.xhtml#escaped-character)

‌ quoted-text-item →
\(

‌ quoted-text-item → Any Unicode extended grapheme cluster except
", U+000A, or U+000D

‌ escaped-character → \0
\n

‌ escaped-character →
\x[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)

‌ escaped-character →
\u[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)

‌ escaped-character →
\U[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)[hexadecimal-digit](LexicalStructure.xhtml#hexadecimal-digit)

Grammar of operators

‌ operator →
[operator-character](LexicalStructure.xhtml#operator-character)[operator](LexicalStructure.xhtml#operator)~opt~

‌ operator-character → /
+
>
.

‌ binary-operator → [operator](LexicalStructure.xhtml#operator)

‌ prefix-operator → [operator](LexicalStructure.xhtml#operator)

‌ postfix-operator → [operator](LexicalStructure.xhtml#operator)

‌

### Types 

Grammar of a type

‌ type → [array-type](Types.xhtml#array-type)
[function-type](Types.xhtml#function-type)
[type-identifier](Types.xhtml#type-identifier)
[tuple-type](Types.xhtml#tuple-type)
[optional-type](Types.xhtml#optional-type)
[implicitly-unwrapped-optional-type](Types.xhtml#implicitly-unwrapped-optional-type)
[protocol-composition-type](Types.xhtml#protocol-composition-type)
[metatype-type](Types.xhtml#metatype-type)

Grammar of a type annotation

‌ type-annotation →
:[attributes](Attributes.xhtml#attributes)~opt~[type](Types.xhtml#type)

Grammar of a type identifier

‌ type-identifier →
[type-name](Types.xhtml#type-name)[generic-argument-clause](GenericParametersAndArguments.xhtml#generic-argument-clause)~opt~
[type-name](Types.xhtml#type-name)[generic-argument-clause](GenericParametersAndArguments.xhtml#generic-argument-clause)~opt~.[type-identifier](Types.xhtml#type-identifier)

‌ type-name → [identifier](LexicalStructure.xhtml#identifier)

Grammar of a tuple type

‌ tuple-type →
(

‌ tuple-type-body →
[tuple-type-element-list](Types.xhtml#tuple-type-element-list)...~opt~

‌ tuple-type-element-list →
[tuple-type-element](Types.xhtml#tuple-type-element)
[tuple-type-element](Types.xhtml#tuple-type-element),[tuple-type-element-list](Types.xhtml#tuple-type-element-list)

‌ tuple-type-element →
[attributes](Attributes.xhtml#attributes)~opt~inout~opt~[type](Types.xhtml#type)
inout~opt~[element-name](Types.xhtml#element-name)[type-annotation](Types.xhtml#type-annotation)

‌ element-name → [identifier](LexicalStructure.xhtml#identifier)

Grammar of a function type

‌ function-type →
[type](Types.xhtml#type)->[type](Types.xhtml#type)

Grammar of an array type

‌ array-type → [type](Types.xhtml#type)[
[array-type](Types.xhtml#array-type)[

Grammar of an optional type

‌ optional-type → [type](Types.xhtml#type)?

Grammar of an implicitly unwrapped optional type

‌ implicitly-unwrapped-optional-type →
[type](Types.xhtml#type)!

Grammar of a protocol composition type

‌ protocol-composition-type →
protocol

‌ protocol-identifier-list →
[protocol-identifier](Types.xhtml#protocol-identifier)
[protocol-identifier](Types.xhtml#protocol-identifier),[protocol-identifier-list](Types.xhtml#protocol-identifier-list)

‌ protocol-identifier → [type-identifier](Types.xhtml#type-identifier)

Grammar of a metatype type

‌ metatype-type → [type](Types.xhtml#type).
[type](Types.xhtml#type).

Grammar of a type inheritance clause

‌ type-inheritance-clause →
:[type-inheritance-list](Types.xhtml#type-inheritance-list)

‌ type-inheritance-list → [type-identifier](Types.xhtml#type-identifier)
[type-identifier](Types.xhtml#type-identifier),[type-inheritance-list](Types.xhtml#type-inheritance-list)
