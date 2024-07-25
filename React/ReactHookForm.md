# React-Hook-Form

-   library for managing form state and validation in React applications using hooks
    `npm install react-hook-form`
    `npm i -D @hookform/devetools`: it is used to visualize the validations
    `npm i yup`: it is used for schema validations
    `npm i @hookform/resolvers`: bridges react-hook-form and yup

```jsx
import { useForm, useFieldArray } from "react-hook-form";
import { DevTool } from "@hookform/devtools";
import { yupResolver } from "@hookform/resolvers/yup";
import * as yup from "yup";

const schema = yup.object({
    username: yup.string().require(required_msg),
});

export default function App() {
    const form = useForm({
        // default values
        defaultValues: {
            username: "",
            // nested objects
            social: {
                facebook: "",
            },
            // static arrays
            phoneNumbers: ["", ""],
            // dynamic array
            phNumbers: [{ number: "" }],
            //number input
            age: 0,
            dob: Date.now(),
        },
        resolver: yupResolver(schema),
        mode: mode_val, //default is onSubmit, can be changed for eg: onBlur, onTouch, onChange, all
        // we can also create an async function async function which fetches data and prepopulate default values as desired
        defaultValues: async () => {
            // fetch data
            return {
                username: data.username,
            };
        },
    });
    const {
        register,
        control,
        handleSubmit,
        formState,
        watch,
        getValues,
        setValue,
        reset,
        trigger, //manually trigerrs validation
    } = form;
    const {
        error,
        touchedFields,
        dirtyFields,
        isDirty,
        isValid,
        isSubmitting, //default is false and set to true when form is submitting and then false when submission is completed
        isSubmitted, //default is false and set to false when form is submitting and then true when submission is completed
        isSubmitSuccessful, // default is false and set to true when submission is successful
        submitCount, //default is 0 and tracks number of times form is submitted
    } = formState;
    // dynamic array
    const { fields, append } = useFieldArray({
        name: "phNumbers",
        control,
    });
    // const { name, ref, onChange, onBlur } = register("username");
    const onSubmit = (data) => {
        console.log("Form Submitted", data);
    };
    const onError = (error) => {
        console.log("Error", error);
    };

    const handleGetValues = () => {
        // if no parameter is passed it will get entire form
        console.log(getValues("username"));
    };

    const handleSetValues = () => {
        // set the value of first parameter to be second parameter
        setValues("username", "", {
            // validations
            shouldValidate: true,
            shouldDirty: true, //tells whether the user has modified the field or not compared to default values
            shouldTouch: true, // tells whether the user has touched the field or not
        });
    };

    // watches for any changes in the specified field
    // if no parameter is passed it will watch entire form
    const watchedValue = watch("username");
    return (
        <>
            <form onSubmit={handleSubmit(onSubmit, onError)} noValidate>
                {
                    // 1st way to implement react-hook-form
                    <input
                        type="text"
                        id="username"
                        name={name}
                        ref={ref}
                        onChange={onChange}
                        onBlur={onBlur}
                    />
                }
                {
                    // 2nd way to implement react-hook-form
                    <>
                        <input
                            type="text"
                            id="username"
                            {...register("username", {
                                required: {
                                    value: true,
                                    message: "username is required",
                                },
                                pattern: {
                                    value: regex,
                                    message: "Invalid",
                                },
                                validate: {
                                    //custom validations
                                    notAdmin: (fieldValue) => {
                                        return fieldValue !== "";
                                    },
                                    // async validations
                                    emailAvailable: async (fieldValue) => {
                                        const resp = fetch_response;
                                        // further validations
                                    },
                                },
                            })}
                        />
                        {
                            // Display error
                            <p>{error.username?.message}</p>
                        }
                    </>
                }
                {
                    // useForm convert any type of input to string input, in order to persist Number input
                    <input
                        type="number"
                        id="age"
                        {...register("age", {
                            valueAsNumber: true,
                            required: {
                                value: true,
                                message: "age is required",
                            },
                        })}
                    />
                }
                {
                    // Date input
                    <input
                        type="date"
                        id="dob"
                        {...register("dob", {
                            valueAsDate: true,
                            required: {
                                value: true,
                                message: "dob is required",
                            },
                        })}
                    />
                }

                <input
                    type="text"
                    id="facebook"
                    {...register("social.facebook", {
                        disabled: true, //cannot interact with the field and validations is also disabled
                        // we can use conditions to disable the field as desired
                    })}
                />
                {
                    // Static array implementation
                    <>
                        <input
                            type="text"
                            id="primaryPhone"
                            {...register("phoneNumber.0")}
                        />
                        <input
                            type="text"
                            id="secondaryPhone"
                            {...register("phoneNumber.1")}
                        />
                    </>
                }
                {
                    // dynamic array implementation
                    <>
                        <div>
                            {fields.map((field, index) => {
                                return (
                                    <div key={field.id}>
                                        <input
                                            type="text"
                                            {...register(
                                                `phNumbers.${index}.number`
                                            )}
                                        />
                                        {index > 0 && (
                                            <button
                                                type="button"
                                                onClick={() => remove(index)}
                                            >
                                                Remove
                                            </button>
                                        )}
                                    </div>
                                );
                            })}
                            <button
                                type="button"
                                onClick={() => append({ number: "" })}
                            >
                                Add phone Number
                            </button>
                        </div>
                    </>
                }
                <button type="submit">Submit</button>
                {
                    // Get Values
                    <button type="button" onCLick={handleGetValues}>
                        Get values
                    </button>
                }
                {
                    // Set Values
                    <button type="button" onCLick={handleSetValues}>
                        Set values
                    </button>
                }
                {
                    // Manually triggers validation
                    <button
                        type="button"
                        onCLick={() => {
                            trigger();
                        }} // if parameter is passed it will trigger validations for that field only
                    >
                        Set values
                    </button>
                }
                <button type="button" onClick={() => reset()}>
                    Reset
                </button>
            </form>
            <DevTool control={control} />
        </>
    );
}
```
