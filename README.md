Go JavaScript Bindings
======================

Highly experiemental, I'm not even sure these work currently. Original author is Robery Johnstone, and his mercurial repository can be found at https://bitbucket.org/rj/golang-javascriptcore/. I have updated the bindings to work with the latest changes to the reflect API, bits of it manually. The entire test suite minus one function (finally!) passes.

There's no documentation, because the original had no documentation. If I find a use for this beyond curiousity, I might add that as I go. Below is a dump of all the available functions, generated by godoc:

package gojs
import "github.com/crazy2be/gojs"

Constants
---------

	const (
			TypeUndefined = 0
			TypeNull      = iota
			TypeBoolean   = iota
			TypeNumber    = iota
			TypeString    = iota
			TypeObject    = iota
	)

	const (
			PropertyAttributeNone       = 0
			PropertyAttributeReadOnly   = 1 << 1
			PropertyAttributeDontEnum   = 1 << 2
			PropertyAttributeDontDelete = 1 << 3
	)

	const (
			ClassAttributeNone                 = 0
			ClassAttributeNoAutomaticPrototype = 1 << 1
	)


Types
-----

### Context

	type Context struct {

	}

func NewContext() *Context

func (ctx *Context) CallAsConstructor(obj *Object, parameters []*Value) (*Value, *Value)

func (ctx *Context) CallAsFunction(obj *Object, thisObject *Object, parameters []*Value) (*Value, *Value)

func (ctx *Context) CheckScriptSyntax(script string, source_url string, startingLineNumber int) *Value

func (ctx *Context) CopyPropertyNames(obj *Object) *PropertyNameArray

func (ctx *Context) DeleteProperty(obj *Object, name string) (bool, *Value)

func (ctx *Context) EvaluateScript(script string, obj *Object, source_url string, startingLineNumber int) (*Value, *Value)

func (ctx *Context) GarbageCollect()

func (ctx *Context) GetProperty(obj *Object, name string) (*Value, *Value)

func (ctx *Context) GetPropertyAtIndex(obj *Object, index uint16) (*Value, *Value)

func (ctx *Context) GetPrototype(obj *Object) *Value

func (ctx *Context) GlobalObject() *Object

func (ctx *Context) HasProperty(obj *Object, name string) bool

func (ctx *Context) IsBoolean(v *Value) bool

func (ctx *Context) IsConstructor(obj *Object) bool

func (ctx *Context) IsEqual(a *Value, b *Value) (bool, *Value)

func (ctx *Context) IsFunction(obj *Object) bool

func (ctx *Context) IsNull(v *Value) bool

func (ctx *Context) IsNumber(v *Value) bool

func (ctx *Context) IsObject(v *Value) bool

func (ctx *Context) IsStrictEqual(a *Value, b *Value) bool

func (ctx *Context) IsString(v *Value) bool

func (ctx *Context) IsUndefined(v *Value) bool

func (ctx *Context) NewArray(items []*Value) (*Object, *Value)

func (ctx *Context) NewBooleanValue(value bool) *Value

func (ctx *Context) NewDate() (*Object, *Value)

func (ctx *Context) NewDateWithMilliseconds(milliseconds float64) (*Object, *Value)

func (ctx *Context) NewDateWithString(date string) (*Object, *Value)

func (ctx *Context) NewError(message string) (*Object, *Value)

func (ctx *Context) NewFunction(name string, parameters []string, body string, source_url string, starting_line_number int) (*Object, *Value)

func (ctx *Context) NewFunctionWithCallback(callback GoFunctionCallback) *Object

func (ctx *Context) NewFunctionWithNative(fn interface{}) *Object

func (ctx *Context) NewNativeObject(obj interface{}) *Object

func (ctx *Context) NewNullValue() *Value

func (ctx *Context) NewNumberValue(value float64) *Value

func (ctx *Context) NewObject() *Object

func (ctx *Context) NewRegExp(regex string) (*Object, *Value)

func (ctx *Context) NewRegExpFromValues(parameters []*Value) (*Object, *Value)

func (ctx *Context) NewStringValue(value string) *Value

func (ctx *Context) NewUndefinedValue() *Value

func (ctx *Context) NewValue(value interface{}) *Value

func (ctx *Context) ProtectValue(ref *Value)

func (ctx *Context) Release()

func (ctx *Context) Retain()

func (ctx *Context) SetProperty(obj *Object, name string, rhs *Value, attributes uint8) *Value

func (ctx *Context) SetPropertyAtIndex(obj *Object, index uint16, rhs *Value) *Value

func (ctx *Context) SetPrototype(obj *Object, rhs *Value)

func (ctx *Context) ToBoolean(ref *Value) bool

func (ctx *Context) ToNumber(ref *Value) (num float64, err *Value)

func (ctx *Context) ToNumberOrDie(ref *Value) float64

func (ctx *Context) ToObject(ref *Value) (obj *Object, err *Value)

func (ctx *Context) ToObjectOrDie(ref *Value) *Object

func (ctx *Context) ToString(ref *Value) (str string, err *Value)

func (ctx *Context) ToStringOrDie(ref *Value) string

func (ctx *Context) UnProtectValue(ref *Value)

func (ctx *Context) ValueType(v *Value) uint8

### ContextGroup

	type ContextGroup struct {

	}

### Error

	type Error struct {
			Name    string
			Message string
			Context *Context
			Value   *Value
	}

func (e *Error) String() string

### GlobalContext

	type GlobalContext Context

### GoFunctionCallback

type GoFunctionCallback func(ctx *Context, obj *Object, thisObject *Object, arguments []*Value) (ret *Value)

### Object

	type Object struct {

	}

func (obj *Object) GetPrivate() unsafe.Pointer

func (obj *Object) SetPrivate(data unsafe.Pointer) bool

func (obj *Object) ToValue() *Value

### PropertyNameArray

	type PropertyNameArray struct {

	}

func (ref *PropertyNameArray) Count() uint16

func (ref *PropertyNameArray) NameAtIndex(index uint16) string

func (ref *PropertyNameArray) Release()

func (ref *PropertyNameArray) Retain()

### String

	type String struct {

	}

func NewString(value string) *String

func (ref *String) Equal(rhs *String) bool

func (ref *String) EqualToString(rhs string) bool

func (ref *String) Length() uint32

func (ref *String) Release()

func (ref *String) Retain()

func (ref *String) String() string

### Stringer

	type Stringer interface {
			String() string
	}

### Value

	type Value struct {

	}