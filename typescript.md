1. [Typescript](http://www.typescriptlang.org/)
	1. compile to javascript languages
		1. CoffeeScript
		1. GWT
		1. Dart
		1. Many others
	1. Advantages
		1. Backed by Microsoft
		1. Developed by [Anders Hejlsberg](http://en.wikipedia.org/wiki/Anders_Hejlsberg)
		1. Superset of Javascript (use existing librarys)
		1. ECMAScript 6 standard (forward compatiblity)
		1. Relation with AngularJS
		1. Debugging
1. Install
	1. Node.js
	1. npm install -g typescript
1. Features
	1. types: number, string, boolean, Array, Enum, Void, function, any

			var num: number = 1;
			var str: string = 'string';
			var bool: boolean = false;
			var arr: Array<string> = ['abc', 'ddd'];
			var arrNum: number[] = [1,2,3];
			enum Day {SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY};
			var day: Day = Day.MONDAY;
			var any: any = 3;
			any = 'foo';
			var func: (a:number, b:number)=>number;
			function add(left: number, right: number): number {
				return left + right;
			}
			func = add;
			
	1. Function
		1. Optional parameters
					
					function foo(param1: number, param2?: number) {
						// ...
					}
					
		2. Default parameters values
		
					function foo(param1: number, param2 = 0) {
						// ...
					}
					
	1. [Declaration files](https://github.com/borisyankov/DefinitelyTyped)
	1. Interface
		1. Properties don't have to be in order
		2. Properties must be present and match the types
		3. Optional properties prop?: string
					
			    interface IFormController {

			        /**
			         * Indexer which should return ng.INgModelController for most properties but cannot because of "All named properties must be assignable to string indexer type" constraint - see https://github.com/Microsoft/TypeScript/issues/272
			         */
			        [name: string]: any;

			        $pristine: boolean;
			        $dirty: boolean;
			        $valid: boolean;
			        $invalid: boolean;
			        $submitted: boolean;
			        $error: any;
			        $addControl(control: INgModelController): void;
			        $removeControl(control: INgModelController): void;
			        $setValidity(validationErrorKey: string, isValid: boolean, control: INgModelController): void;
			        $setDirty(): void;
			        $setPristine(): void;
			        $commitViewValue(): void;
			        $rollbackViewValue(): void;
			        $setSubmitted(): void;
			        $setUntouched(): void;
			    }
	
	1. Class
		1. Members are public by default
		1. Private members are only at compilation stage

				class Animal {
					private foo: boolean;
				    name:string; // public by default
				    constructor(theName: string) { this.name = theName; }
				    move(meters: number = 0) {
				        alert(this.name + " moved " + meters + "m.");
				    }
				}

				class Snake extends Animal {
				    constructor(name: string) { super(name); }
				    move(meters = 5) {
				        alert("Slithering...");
				        super.move(meters);
				    }
				}

				class Horse extends Animal {
				    constructor(name: string) { super(name); }
				    move(meters = 45) {
				        alert("Galloping...");
				        super.move(meters);
				    }
				}

				var sam = new Snake("Sammy the Python");
				var tom: Animal = new Horse("Tommy the Palomino");

				sam.move();
				tom.move(34);
				
		1. Lambda and this
				
					return ()=> {
					//return function() {
						console.log(this);
					}
	
	1. Module
		1. namespace, package
		1. export
